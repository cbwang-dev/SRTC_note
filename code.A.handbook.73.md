```ada
package Temperature_Control is
	subtype Temperature is Integer range 0 .. 100;
	Sensor_Dead, Actuator_Dead : exception;

	procedure Set_Temperature(New_Temp : in Temperature);
	-- raises Actuator_Dead
	function Read_Temperature return Temperature;
	-- raises Sensor_Dead
end Temperature_Control;

package body Temperature_Control is
	procedure Set_Temperature(New_Temp : in Temperature) is
	begin
		-- inform actuator of new temperature
		if No_Response then
			raise Actuator_Dead;
		end if;
	end Set_Temperature;

	function Read_Temperature return Temperature is
	begin
		-- read sensor
		if No_Response then
			raise Sensor_Dead;
		end if;
		-- calculate temperature
		return Reading;

	exception
		when Constraint_Error =>
			-- the temperature has gone outside
			-- its expected range;
			-- take some appropriate action
	end Read_Temperature;
begin
	-- start initialization of package
	Set_Temperature(Initial_Reading);
exception
	when Actuator_Dead => 
		-- during the initialization if the exception is thrown then is handled
		-- take some corrective action
end Temperature_Control;
```

**General Questions**

-   In what programming language is this written? 
	-   Ada
        
-   What does the piece of code do?
	-   Control temperature of a room by using a sensor to read the temperature and adjust it (if necessary) by using an actuator. When the package is initialized, the function `Set_Temperature` is called. If it raises an `Actuator_Dead` error at that moment, it will be handled. Otherwise, if the function `Set_Temperature` is called at any other moment in time after the initialization, no error handling is provided fot `Actuator_Dead` error. 
	-   The handler `Actuator_Dead` given in the initialization section of the package will only catch the exception when the procedure is called from the initialization code. 
	-   If the code which initialized a package body itself raises an exception which is not handled locally, the exception is propagated to the point where the package came into scope.
        
-   This is an example of what?
	-   This is an example of 2 exceptions in one piece of Ada code.
        
-   What is “special” in this piece of code?
	-   An exception raised and not handled by a subprogram is propagated to the caller of the subprogram. Therefore, such an exception will *only be handled by the initialization code if it itself called the subprogram*.
		
-   Why is this included in the book.
    

**Question: Why are there two place where exceptions are handled?**

**Question: Where is the exception `Sensor_Dead` caught?**

**Question: How would you write this in another programming language?**