---
layout: post
title:  "Testing Jekyll"
date:   2025-01-17 17:31:20 -0800
categories: jekyll update
---

Test page for C/C++ code snippets.

The below code is an example of how to use the RP2040 ADC to measure both the internal temperature sensor and vSYS.

pico_stlib and hardware_adc must be added to the cmake file in order to use the adc.

{% highlight cpp  %}
target_link_libraries(... pico_stdlib hardware_adc)
{% endhighlight %}

Below is simple code to measure and write the results over serial UART/USB depending on your settings.

{% highlight cpp linenos  %}
#include <stdio.h>
#include "pico/stdlib.h"
#include "hardware/adc.h"

int main()
{
    stdio_init_all();

    gpio_init(29); //gpio_29 is connected to vSys

    //enable input for gpio_29 to connect vsys to adc
    gpio_set_input_enabled(29, true); 

     //turn off pull-up/pull-down resistors. pull-down on by default gives 1.25V readings.
    gpio_set_pulls(29, false, false);

    //configure ADC
    adc_init();
    adc_set_temp_sensor_enabled(true); // enable internal temp sensor on ADC channel 4. 
    adc_select_input(4);

    while(1)
    {
        //select temp sx channel.
        adc_select_input(4); 
        uint16_t raw = adc_read();
        //conversion for 12bit number (max val 4096)
        const float conversion = 3.3f / (1<<12); 
        float voltage = raw * conversion; 
        //voltage to temperature conversion formula from RP2040 datasheet
        float temperature = 27 - (voltage - 0.706)/0.001721; 
        printf("Temperature: %f C\n", temperature);
        sleep_ms(500);

        //gpio_29/vSys is connected to ADC on channel 3.
        adc_select_input(3); 
        uint16_t rawV = adc_read();
        float v = rawV * conversion; 
        //100k/200k resistor divider on input. multiply by 3.
        float vSys = v * 3; 
        printf("Vsys: %f V\n", vSys);
    }
}
{% endhighlight %}

![Image]({{"assets/images/rp2040.jpg",  | relative_url }})