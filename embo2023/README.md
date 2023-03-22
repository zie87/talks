# Lessons Learned for Reusable Firmware

MCUs get more and more powerful and get more responsibilities in a system. 
Each device from our company contains one or more MCUs, which needs to be 
maintained for at least 10 years after the release. To keep the development 
and maintenance costs small it is necessary to reuse as much software as 
possible. In my talk I want to provide you the lessons I learned for writing 
reusable, hardware and operating system independent software. This contains 
hints about the hard- and middleware abstraction and also how to structure the 
business logic that it can be reused without changes between different firmware 
projects.

## build markdown presentation

```sh
pandoc -t beamer 00_title.md 01_introduction.md 02_hal.md 03_middleware.md 04_business_logic.md 05_end.md -o talk.pdf
```
