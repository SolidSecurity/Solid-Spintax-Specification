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
##### Possible Outputs (36 total):
 - "My height is 4'8"."
 - "My height is 6'3"."

### 1.3 Shuffle Switches
*A shuffle switch is specified using curly braces ({}) with an exclamation point (!) prefacing the braces.

##### Basic Example:
> I went to the store. I bought !{apples|cheese|oranges|a gallon of milk} and some bacon.
##### Possible Outputs (24 Total)
 - "I went to the store. I bought apples, oranges, a gallon of milk, cheese, and some bacon.
 - "I went to the store. I bought cheese, a gallon of milk, oranges, apples, and some bacon.
 
##### Advanced Example:
> We need to order !{{2-4} Bricks|{3-5} slats of hardwood|{strong|industrial strength|good} cement} and some tile.
##### Possible Outcomes (1944 total):
 - "We need to order 2 bricks, 4 slats of hardwood, industrial strength cement, and some tile.
 - "We need to order 3 bricks, 5 slats of hardwood, strong cement, and some tile."

## 2. Structure
### 2.1. Nested Switches
Nested switches are created by specifying a switch within the body of a string switch. Solid's Spintax supports unlimited nesting depth.

##### Basic Example:
> A phone that costs {{100-499} is too cheap|{500-899} is just right|{900-1499} is too expensive}.
##### Possible Outputs (1400 total):
 - "A phone that costs $393 is too cheap."
 - "A phone that costs $582 is too just right."
 - "A phone that costs $1243 is too expensive."

##### Advanced Example:
> Tailspin is {{an advanced|a {vital|sophisticated}} leak-{mitigation|detection} tool|an open source software library}.
##### Possible Outputs (7 total):
 - "Tailspin is an open source software library."
 - "Tailspin is an advanced leak-detection tool."
 - "Tailspin is a sophisticated leak-mitigation tool."

### 2.2. Optional Content
Optional content is specified by adding an empty option to a switch, usually by adding a pipe (|) immediately after the opening brace.

##### Basic Example:
> This is {|very |so }easy!
##### Possible Outputs (3 total):
 - "This is easy!"
 - "This is very easy!"
 - "This is so easy!"

##### Advanced Example:
> Solid{| Security} is a {| certified}{| private} {|cyber}security{| services} {provider|company}.
##### Possible Outputs (64 total):
 - "Solid is a security company."
 - "Solid Security is a certified private cybersecurity services provider."
 - "Solid is a private security services company."

## 3. Advanced Features
### 3.1. Global Switches
*A global switch is specified using an at symbol (@) followed by curly braces ({}) with options separated by a vertical bar (|). Two global switches must have an identical set of options in order to guarantee the same output.*

Global switches allow you to specify a set of options that, once selected from, will return the same result for the entire document.

##### Basic Example:
> Introducing project @{Purple Phoenix|Golden Eagle}. Project @{Purple Phoenix|Golden Eagle} is a new security initiative from Solid Security. Our goal with project @{Purple Phoenix|Golden Eagle} is to...
##### Possible Outputs (2 total):
 - "Introducing project Purple Phoenix. Project Purple Phoenix is a new security initiative from Solid Security. Our goal with project Purple Phoenix is to..."
 - "Introducing project Golden Eagle. Project Golden Eagle is a new security initiative from Solid Security. Our goal with project Golden Eagle is to..."

### 3.2. Escaped Characters
*A backslash (\\) character can be used before special characters like at symbols (@), curly braces ({}), and vertical bars (|) to prevent them from being interpreted as switches or other special syntactic elements.*

Escaped characters allow you to use characters like curly braces ({}), at symbols (@), and vertical bars (|) as part of the final text rather than having them interpreted as a special instruction.

##### Basic Example:
> Email: \{hello\@solidsecurity.co\}
##### Possible Outputs (1 total):
 - "Email: {hello@solidsecurity.co}"
