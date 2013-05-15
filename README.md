# node-xcode

> parser/toolkit for xcodeproj project files. Too many bugs, not recommended to use. You can use the following python script to modify your project.pbxproj
> https://gist.github.com/tanhongxu/7a6078f6f7cea9069972

Allows you to edit xcodeproject files and write them back out.

## Example

    // API is a bit wonky right now
    var xcode = require('xcode'),
        fs = require('fs'),
        projectPath = 'myproject.xcodeproj/project.pbxproj',
        myProj = xcode.project(projectPath);

    // parsing is async, in a different process
    myProj.parse(function (err) {
        myProj.addHeaderFile('foo.h');
        myProj.addSourceFile('foo.m');
        myProj.addFramework('FooKit.framework');
        
        fs.writeFileSync(projectPath, myProj.writeSync());
        console.log('new project written');
    });

## License

MIT
