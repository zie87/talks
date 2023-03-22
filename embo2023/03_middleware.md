# Middleware Abstraction: Thread

## Zephyr
\scriptsize
```cpp
k_tid_t k_thread_create(struct k_thread *new_thread, 
                        k_thread_stack_t *stack, 
                        size_t stack_size, 
                        k_thread_entry_t entry, 
                        void *p1, void *p2, void *p3, 
                        int prio, 
                        uint32_t options, 
                        k_timeout_t delay);
```
\normalsize

## FreeRTOS 
\scriptsize
```cpp
BaseType_t xTaskCreate( TaskFunction_t pvTaskCode,
                        const char * const pcName,
                        configSTACK_DEPTH_TYPE usStackDepth,
                        void *pvParameters,
                        UBaseType_t uxPriority,
                        TaskHandle_t *pxCreatedTask);
```
\normalsize

# Middleware Abstraction: Thread

## thread abstraction
\scriptsize
```cpp
thread::thread(const thread_cfg& cfg, 
               entry_type entry);
```
\normalsize

## thread use 
\scriptsize
```cpp
struct component  {
    component(const thread_cfg& cfg) noexcept 
        : m_thread(cfg, /*...*/) {};
    /*...*/
    thread m_thread;
};
/*...*/
class system_setup  {
    /*...*/
    thread_cfg m_thread_cfg{stack_cfg(addr, size), thread_prio::low};
    component  m_component{m_thread_cfg};
};
```
\normalsize

# Middleware Abstraction: STL

## backport
\scriptsize
```cpp
#if __cplusplus >= 202002L
    #include <span>
#else 
    #include "span_backport.hpp"
#endif
```
\normalsize

## freestanding
\scriptsize
```cpp
namespace mwa {
    template <class R, class P = ::mwa::ratio<1>>
    using duration = std::chrono::duration<R, P>;
}
```
\normalsize


# Middleware Abstraction

## Summary

* Lead business logic design
* Consider Host OS from the beginning
* Take care about behavior relevant parts
    * Allow resources to be handled outside
    * Separate configuration and creation
* Provide only what is necessary
