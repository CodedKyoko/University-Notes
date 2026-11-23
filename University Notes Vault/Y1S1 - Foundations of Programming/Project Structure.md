UniversityApp/
	UniversityApp.csproj
	Program.cs
	Models/
	Student.cs
	Course.cs

The project file (.csproj) describes the project and its dependancies.
Program.cs contains the 
- Classes can live in separate files; related files can be grouped in folders
- A useful convention is one main class per file, with matching names

Files, Projects and Solutions.

>[!File]
> Contains source code, such as class definition.

>[!Project]
> Groups source and dependencies to build an app or library
>
>>[!Note]
>>A folder is not automatically a separate project, a A .csproj file defines a project.

>[!Solution]
> Can group multiple related projects, such as an app and its tests.

## Namespaces

A namespace organises names and helps avoid conflicts

```cs
namespace University.Models {

	public class Student { }
}

namespace Library.Models {

	public class Student { }
}
```

The 2 `Student` classes are 2 separate classes
University.Models.Student
Library.Models.Student

You can import a name space by using the term `using` which allows you to make use of the values in a Namespace, without specifying the entire Namespace path each time.

- Multiple classes and files can use the same Namespace
- A namespace is a logical name; it is not the same thing as a folder
- Folders can mirror namespaces for organisation, but moving a file does not automatically change its namespace decleration

