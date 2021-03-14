# Winforms DI Template
A starter Windows Forms project that includes dependency injection.

This starter project is suitable for people who want to make use of DI with Windows Forms Application (.net5).


Notes.
1) In order to open a child Form from parent Form here is a sample use    
        
        CurrentHost = Host.CreateDefaultBuilder()
                .ConfigureServices((context, services) =>
                {
                    services.AddScoped<EntryForm>();
                    //First you need to add the child Form in DI as follows
                    services.AddTransient<ChildForm>();
                })
                .UseSerilog()
                .Build();
  
     And in EntryForm you simply add this line of code in a button event for showing the child Form              
              
              var childForm = (ChildForm)Program.CurrentHost.Services.GetService(typeof(ChildForm));
              childForm.Show();
