# tracing-local-time
A patch to fix tracing LocalTime problem.

Tracing-subscribe now has a bug in LocalTime, so build ourselves' to fix it.
In this patch, we use fixed timezone +8 for China usage.
