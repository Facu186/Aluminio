# Aluminio
a#include <stdio.h>
#include "pico/stdlib.h"

int main(void) {
  bool repeating_timer_callback1(struct repeating_timer *t) {
   gpio_put (1, !gpio_get (1));
    return true;
  }

  bool repeating_timer_callback2(struct repeating_timer *t){
   gpio_put (2, !gpio_get (2));
   return true;}

  bool repeating_timer_callback3(struct repeating_timer *t) {
   gpio_put (3, !gpio_get (3));
    return true; }

  bool repeating_timer_callback4(struct repeating_timer *t) {
  gpio_put (4, !gpio_get (4));
   return true; 
}
   int main (void) {
    gpio_init (1);
    gpio_set_dir (1,true);
    gpio_init (2);
    gpio_set_dir (2,true);
    gpio_init (3);
    gpio_set_dir (3,true);
    gpio_init (4);
    gpio_set_dir (4,true);
    struct repeating_timer timer1;
    struct repeating_timer timer2;
    struct repeating_timer timer3;
    struct repeating_timer timer4;
    add_repeating_timer_ms(250, repeating_timer_callback1, NULL, &timer1);
    add_repeating_timer_ms(500, repeating_timer_callback2, NULL, &timer2);
    add_repeating_timer_ms(1000, repeating_timer_callback3, NULL, &timer3);
    add_repeating_timer_ms(2000, repeating_timer_callback4, NULL, &timer4);
    while(1);
    return 0;
   }   
}
