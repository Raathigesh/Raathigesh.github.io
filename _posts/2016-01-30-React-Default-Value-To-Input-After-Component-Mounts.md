---
published: false
---


When you assign values to an input element in React, you can go two ways.

- Assign through the value attribute.
- Assign through the defaultValue attribute.

When the value is set using value attribute, your input box becomes a controlled component. User won't be able to change the value unless there is an onChange handled attached and the value is set back again when ever user types using the component state.

When the value is set using the defaultValue attribute, the value is set as the default or initial value of the input box and user can still go ahead and change it. But the defaultValue will be set if the value is available when the component mounts. If your default value is coming through a prop and if the prop changes after the component mounts, that change won't be reflected in the input box value.