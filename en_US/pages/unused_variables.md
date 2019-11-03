# Unused Variables

In the course of cleaning up code, and removing compiler warnings, you may
find unused variables in the code. This could be either results from functions
that are simply ignored, or code that the author meant to “fill in” later, and
never got around to.

It may be harmless, or may be an indication that something needs fixing. We
don't want to arbitrarily start hacking out unused variables, but we would
like to suppress noisy warnings, so we can keep an eye for warnings in changes
we ARE making to the code. How to suppress these warnings in a safe manner,
but mark them in such a way that we may, at some point in the future, go back
and evaluate them to see if they DO need fixing or deletion?

## Use the preprocessor

If we define this at the top of a file that contains unused variable warnings:

    
    
    #ifdef __GNUC__
    #define UNUSED_VARIABLE __attribute__ ((unused))
    #else
    #define UNUSED_VARIABLE
    #endif

Later on, when we come across a warning that a variable `status` is unused:

    
    
    gint status;
     
    /* ... */
     
    status = write (....);
     
    /* No further mention of status */

We can simply change the declaration to:

    
    
    gint UNUSED_VARIABLE status;

The compiler warning is now suppressed, and, we can simply grep the code at a
later date for `UNUSED_VARIABLE` to find possible areas of improvement.

