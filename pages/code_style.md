# Code style

## Indent style

I would like to use Allman (ANSI) style. Long line is fine too. Recommended
MATE code style is to use spaces instead of tabs, which can make easily
indent issues with different tab width in different editors.

## Type left, name right

Use pointers at the left side.

```
    void* custom_function(char* name);


    int* address = (void*) custom_function((char*) unknown_string);
```

## Void missreading

```
    #define SOME_TYPE_DEF (a) // replace SOME_TYPE_DEF with (a)

    #define SOME_TYPE_DEF(a) // replace SOME_TYPE_DEF(a) with none
```

So these functions should be easy to understand

```
    // define prototype
    long int mycustom_someclass_somefunction(char a);

    // define block code
    long int mycustom_someclass_somefunction(char a)
    {
    	return (long int) some_function(a);
    }
```

## Comments

Use whatever you want.

## Long line is fine too

large declarations show you how much of the stack a function uses, so deal
with it. Next code is right.

```
char* omg_my_application_do_all(struct some_custom_struc* object, int* height, int* width, int* x, int* y, char* title, char* tooltip, char* description, char* sub_description, int flags)
{
	// ...
```

but you can use code like block on #define

```
#define SOME_MACRO_WITH_FUNCTION(x, y, z) \
{ \
	long dist = x * y * z; \
	if (dist <= 0) \
	{ \
		dist = 1; \
		err = DIST_IS_ZERO; \
	} \
	prev_defined = dist; \
}
```

## Use spaces on shell scripts

Do not use tab, use 4 spaces. 2 is too few and 8 is too many. Alignment of
arguments is allowed.

If you want to copy and paste some code and run it in a terminal, press the
tab key and it will try to autocomplete some words.

## Uppercase Vs. Lowcase

Use lowcase for local variables.

Use uppercase for macros.

Use a mix of both on clases, funcions and struct members. Like Java or C#.
