```ada
package Action_X is -- 3 task atomic action
	procedure Code_For_First_Task(--params);
	procedure Code_For_Second_Task(--params);
	procedure Code_For_Third_Task(--params);
end Action_X;

package body Action_X is 
	-- action controller implemented in protected type
	protected Action_Controller is 
		entry First; 
		entry Second; 
		entry Third; 
		entry Finished;
	private
		First_Here  : Boolean := False;
		Second_Here : Boolean := False;
		Third_Here  : Boolean := False;
		Release     : Boolean := False;
	end Action_Controller;
	
	protected body Action_Controller is
		entry First when not First_Here is
		begin
			First_Here := True;
		end First;
		
		entry Second when not Second_Here is
		begin
			Second_Here := True;
		end Second;
		
		entry Third when not Third_Here is
		begin
			Third_Here := True;
		end Third;
		
		entry Finished when Release or Finished'Count = 3 is
		begin
			if Finished'Count = 0 then 
				Release     := False;
				First_Here  := False;
				Second_Here := False;
				Third_Here  := False;
			else
				Release     := True;
			end if;
		end Finished;
	end Action_Controller;
```

This can be used as follows:

```Ada
	procedure Code_For_First_task(--params) is
	begin
		Action_Controller.First;
		-- acquire resources
		-- the action itself, communicates with tasks esecuting
		-- inside the action via reshources
		Action_Controller.Finished;
		-- release resources
	end Code_For_First_Task;

	-- similar for second and third task
begin
	-- any initialization of local resources
end
```

- The action is synchronized by the `Action_Controller` [[protected object]].
	- This ensures that only three tasks can be active in the action at any one time and that they are synchronized at exit. 
- The boolean `Release` is used to program the required release conditions on `Finished`. 
	- The first two calls on `Finished` will be blocked as both parts of the barrier expression are `false`. 
	- When the third call comes, the `Count` attribute will become three; the barrier becomes open and one task will execute the entry body. 
	- The `Release` variable ensures that the other two tasks are both released. 
	- The last task to exit must ensure that the barrier is closed again. 