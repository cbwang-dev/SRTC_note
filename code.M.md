```ada
package Operating_System_Interface is
	type Thread_ID is private;
	type Thread is access procedure; -- a pointer type

	function Create_Thread(Code : Thread) return Thread_ID;
	-- other subprograms for thread interaction
private
	type Thread_ID is ...;
end Operating_System_Interface;

package Processes is
	procedure Pressure_Controller;
	procedure Temp_Controller;
end Processes;

with Data_Types; use Data_Types;
with IO; use IO;
with Control_Procedures; use Control_Procedures;
package body Processes is
	procedure Temp_Controller is
		TR : Temp_Reading;
		HS : Heater_Setting;
	begin
		loop
			Read(TR);
			Temp_Convert(TR,HS);
			Write(HS);
			Write(TR);
		end loop;
	end Temp_Controller;

	procedure Pressure_Controller is
		PR : Pressure_Reading;
		PS : Pressure_Setting;
	begin
		loop
			Read(PR);
			Pressure_Convert(PR,PS);
			Write(PS);
			Write(PR);
		end loop;
	end Pressure_Controller;
end Processes;

with Operating_System_Interface; use Operating_System_Interface;
with Processes; use Processes;
procedure Controller is
	Tc, Pc: Thread_Id;
begin
	-- create the threads
	-- 'Access returns a pointer to the procedure
	Tc := Create_Thread(Temp_Controller'Access);
	Pc := Create_Thread(Pressure_Controller'Access);
end Controller;
```