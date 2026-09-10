1.AttributeError
An AttributeError occurs when code tries to access something that isn’t defined for that object. Think of it like asking a machine to perform a function it doesn’t have.
Example: writing self.fan when the class only has self.fan_speed. Since fan doesn’t exist, Python raises an error. The fix is simply to use the correct attribute name.

2.RecursionError
A RecursionError happens when a function keeps calling itself without a way to stop. This creates an infinite loop until Python halts execution.
In the air conditioner code, the temperature setter was written as: self.temperature = value.Because temperature is a property, this line triggered the setter again, which then called itself repeatedly. The solution was to assign directly to the private variable:self._temperature = value.This stores the value safely without looping back into the setter.

3.Constructor and Setter
The constructor (__init__) is responsible for setting up the object when it’s created. If the constructor assigns directly to the private variable:self._temperature = temperature. The value bypasses any validation logic in the setter. That means invalid values (like 99, if the allowed range is smaller) could slip through.
By using:self.temperature = temperature.The constructor ensures the setter runs, applying validation rules immediately when the object is created. This keeps the object consistent and safe from the start.

4.Energy-Saving Property
The is_energy_saving property should always reflect the current state of the air conditioner. If it relied on a stored value, the information could become outdated when the temperature changes.
By checking the temperature dynamically each time the property is accessed, the result is always accurate. This design ensures that the energy‑saving status updates automatically with the latest conditions.

