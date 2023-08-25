# TIL

## 2023-08-24

The KHR version of Vulkan functionality may not be as universal as the non-KHR version.

While dealing with
[vkGetPhysicalDeviceImageFormatProperties2](https://registry.khronos.org/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceImageFormatProperties2.html)
I realized that I was working with a device and a test case where the instance was not storing the
function pointer for the 2KHR command but was for the base 2 command. This struck me as odd since
the KHR version is almost always older than the core version. In this case the command was made
core in vulkan 1.1, whereas it previously existed in the extension
VK_KHR_get_physical_device_properties2.

I had hither-to-for been assuming that the older KHR command would have wider support, and that it
was safer to query for that one alone. Well, no, there are many situations where a device will
support the newer core version without the previous extension. The test or app also needs to
enable the extension, which this particular test did not.

The only safe thing is to check for both and use whichever comes up.

## 2023-08-21

I can do a 10 rep squat with 75 kilograms.

## 2023-08-20

Hurricanes can make land over California.

As I type Hurricane Hillary is on the way to the California coast after spending multiple days
sitting over the Mexican coast.
