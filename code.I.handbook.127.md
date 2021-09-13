```ada
with Data_Types; use Data_Types;
with IO; use IO;
with Control_Procedures; use Control_Procedures;
procedure Controller is
	task Temp_Controller;
	task Pressure_Controller;

	task body Temp_Controller is
		TR : Temp_Reading; HS : Heater_Setting;
	begin
		loop
			Read(TR);
			Temp_Convert(TR,HS);
			Write(HS);
			Write(TR);
		end loop;
	end Temp_Controller;

	task body Pressure_Controller is
		PR : Pressure_Reading; PS : Pressure_Setting;
	begin
		loop
			Read(PR);
			Pressure_Convert(PR,PS);
			Write(PS);
			Write(PR);
		end loop;
	end Pressure_Controller;

begin 
	null;  -- Temp_Controller and Pressure_Controller
		   -- have started their executions
end Controller;
```

**concurrent** control program in Ada. Split the computationally intensive sections (`Temp_Convert` and `Pressure_Convert`) into a number of distinctive sections. more efficient than **sequential** code below. 

```ada
with Data_Types; use Data_Types;
with IO; use IO;
with Control_Procedures; use Control_Procedures;
procedure Controller is
	TR : Temp_Reading; 
	HS : Heater_Setting;
	PR : Pressure_Reading; 
	PS : Pressure_Setting;
begin
	loop
		Read(TR); -- from ADC
		Temp_Convert(TR,HS); -- convert reading to setting
		Write(HS); -- to switch
		Write(TR); -- to console
		Read(PR); --as above for pressure
		Pressure_Convert(PR,PS);
		Write(PS);
		Write(PR);
	end loop; -- infinite loop, common in embedded systems
end Controller;
```

In the code above, it is assumed that the temperature and pressure readings must be taken at the same rate. 

while waiting to read a temperature no attention can be given to pressure (and vice versa).

Moreover, if there is a system failure that results in, say, control never returning from the temperature `Read`, then in addition to this problem, no further pressure `Read`s would be taken. 
