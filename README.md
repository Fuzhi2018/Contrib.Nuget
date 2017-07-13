Contrib.Nuget
=============

Project extending nuget with additional features:

## Baseclass.Contrib.Nuget.Output

Treats the "output" folder as an additional special folder and copies its content to the build folder

http://www.nuget.org/packages/Baseclass.Contrib.Nuget.Output/

Add this package to your packages dependencies

	<dependencies>
            <dependency id="Baseclass.Contrib.Nuget.Output" />
	</dependencies>

and every file you add to your packages output folder will be copied at build time to the projects output folder.

	<files>
        <file src="output\native.dll" target="output\native.dll" />
		<file src="output\autoresolved.dll" target="output\autoresolved.dll" />
		<file src="output\doc\readme.txt" target="output\doc\readme.txt" />
    </files>

Benefits:

If you are dynamically loading components or your depend on some native dll's you need them to be copied to projects output folder. This package does exactly this!
	
Step by step example: http://www.baseclass.ch/blog/Lists/Beitraege/Post.aspx?ID=6&mobile=0

## Baseclass.Contrib.Nuget.Linked

Treats the "Linked" folder as an additional special folder and links its content as existing to the current project.

http://www.nuget.org/packages/Baseclass.Contrib.Nuget.Linked/

Add this package to your packages dependencies

	<dependencies>
            <dependency id="Baseclass.Contrib.Nuget.Linked" />
	</dependencies>
	
Add the following line to your install.ps1 script in the tools folder:

	Add-LinkedAsExisting $installPath $project $package

Add the following line to your uninstall.ps1 script in the tools folder:

	Remove-LinkedAsExisting $installPath $project $package

and every file you add to your packages Linked folder will be linked as existing in the current project.

	<files>
        <file src="Linked\CodeTemplates\Test\T4TestTemplate.tt" target="Linked\CodeTemplates\Test\T4TestTemplate.tt" />
        <file src="Linked\CodeTemplates\Test\TemplateFileManagerV2.1.ttinclude" target="Linked\CodeTemplates\Test\TemplateFileManagerV2.1.ttinclude" />
        <file src="Linked\Test.txt" target="Linked\Test.txt" />
    </files>
	
TestPackage containing a T4 template and linked Test.txt file can be found at: 

https://github.com/baseclass/Contrib.Nuget/tree/master/TestPackages/TestPackageLinked.1.0.3.nupkg (Click on "View Raw" to download)

Limitation: 
- Option "Create directory for solution" must be checked when creating a project. VS doesn't allow linking existing files that reside directly below the project directory.
- Conflicts with nuget while uninstalling if it's the last package in the solution.

## Baseclass.Contrib.Nuget.GitIgnoreContent

Ignore nuget content files in git:
- Generate entries in the .gitignore file to exclude nuget content files from the source repository
- Restore nuget content files before building (Automatically in VS and manually with a powershell script
- Use Initialize-GitIgnore to add it to an existing solution

Step by step example of usage : http://www.baseclass.ch/blog/Lists/Beitraege/Post.aspx?ID=9&mobile=0
	
[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/370ef518807434c0104ca3fc9f509904 "githalytics.com")](http://githalytics.com/baseclass/Contrib.Nuget)
