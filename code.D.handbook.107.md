```ada
package Arm_Support is
	type Dimension is (Xplane, Yplane, Zplane);
	type Coordinate is new Integer range ...;
	
	procedure Move_Arm(D: Dimension; C: Coordinate);
		-- Moves the arm to C
		
	function New_Setting(D: Dimension) return Coordinate;
		-- returns a new required relative position
		
end Arm_Support;

with Arm_Support; use Arm_Support;
procedure Main is -- main program

	task type Control(Dim : Dimension);
	
	C1 : Control(Xplane);
	C2 : Control(Yplane);
	C3 : Control(Zplane);
	
	task body Control is 
		Position : Coordinate;  -- current position
		Setting  : Coordinate;  -- required relative movement
	begin
		Position := Coordinate'First;  -- rest position
		loop
			Move_Arm(Dim, Position);
			Setting := New_Setting(Dim);
			Position := Position + Setting;
		end loop;
	end Control;
begin
	null;
end Main;
```


Explain the use of the three last lines. 
- The procedure is already running during initialization. 
- parameters can be passed at initialization

concurrent execution in Ada

