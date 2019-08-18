# Solid's Spintax Cheatsheet
This document is intended to serve as a quick reference for the Solid Spintax.

Solid Spintax is an extended and standardized version of the spintax that is used by most spinning software. As such, many of the features outlined below are not supported by all spinners. However, the syntax is designed to be backwards-compatible with existing spintax generators.

This document is not a formal specification &mdash; it's merely intended to be used as an easily-digestable overview of what the format can offer.

## 1. Switches
### 1.1. String Switch
*A string switch is specified using curly braces ({}) with options separated by a vertical bar (|).*

The most basic spintax element is a string switch. The spun text will contain one of the specified options.

##### Basic Example:
> {Hello|Goodbye} World!
##### Possible Outputs (2 total):
 - "Hello World!"
 - "Goodbye World!"

##### Advanced Example:
> {Writing|Creating} {articles|stories} is {an enjoyable|a fun|a rewarding} experience.
##### Possible Outputs (12 total):
 - "Writing stories is a fun experience."
 - "Creating articles is a rewarding experience."
 - "Creating stories is an enjoyable experience."

### 1.2. Integer Switches
*An integer switch is specified using curly braces ({}) with an inclusive upper and lower bound separated by a dash (-).*

An advanced spintax element supported by SolidSpintax is an integer switch.

##### Basic Example:
> The retail price is ${400-500}.
##### Possible Outputs (101 total):
 - "The retail price is $153."
 - "The retail price is $479."

##### Advanced Example:
> My height is {4-6}'{0-11}"
##### Possible Outputs (12 total):
 - "My height is 4'8"."
 - "My height is 6'3"."
