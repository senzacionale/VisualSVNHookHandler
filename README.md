#VisualSVNHookHandler code repo##post-commit-hookCode for a custom post-commit hook executable that can be used with VisualSVN server. There is a project that contains C# versions of the code.Build the project and copy the .exe file from the bin/debug folder in your project to the bin folder in your VisualSVN server installation folder, which in my case was C:\Program Files\VisualSVN Server\bin. Then, open up VisualSVN server and right click on the repository that you want to add the post-commit hook to and click properties.Open the hooks tab and double click on Post-commit hook. It will open a window that you need to paste the following code into. All it does is tell VisualSVN to run the .exe when a commit happens and passes in the required arguments:```csharp"%VISUALSVN_SERVER%bin<name_of_your_built_exe>.exe" "%1" %2 "mail@mail.com,mail2@mail2.com"``` where "mail@mail.com,mail2@mail2.com" are comma separated recipients list.