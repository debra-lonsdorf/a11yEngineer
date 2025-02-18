---
layout: entry
title:  "Number input"
categories: form

keyboard:
  tab: |
    Focus moves visibly to the input
  
mobile:
  swipe: |
    Focus moves to the input, number pad appears

screenreader:
  name:  |
    Purpose is clear
  role:  |
    Identifies itself as a input
  group: |
    Label is read with the input
  state: |
    The input can be required, disabled
---

## Code examples

### Use `type="text"` 
Use `type=text` with `inputmode="numeric"` with a input pattern.

### Don't use `type="number"` 

The `type="number"` input is intended for integers and includes features we don't want like stepper functionality that is a nuisance to everyone. Phone, credit card, pin etc. are not integers.

{% highlight html %}
{% include /examples/input-number.html %}
{% endhighlight %}

{::nomarkdown}
<example>
{% include /examples/input-number.html %}
</example>
{:/}

## Developer notes

### Name
- Include `for="input-id` in each `<label>` label to associate it with the input
- Use `aria-label="Input name"` as a last resort if a `<label>` can't be used
- Don't hide the label on focus

### Role
- Identifies as a text input


### Group
- Include `for="input-id` in each `<label>` label to associate it with the input
- Use `<fieldset>` and `<legend>` to name a group of inputs.

### Focus
- Focus must be visible