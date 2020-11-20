# stanford-cpp-library

Confusingly, not all of the libraries in here are C++.
The relevant libraries are the Java ones, at least for me.

During that code class that I took at d.tech, the people from microsoft used
Stanford's curriculum. Particularly, `spl.jar` and `acm.jar`.

Basically, things didn't work with that library and I kept getting errors about
a missing `GCMDLN.DLL` and I needed to use it for class. I either decompiled
`acm.jar` or found this repo and basically figured out what the problem was.

The entire root of the problem basically boils down to ~~the fact that child
classes do not inherit static methods and because of~~ the API that they wanted to
make where you can write a class without having to write a main method
(processing anyone?), they had to basically escape and reenter.
It's really cursed.

Basically, the main method gets inherited down but there's no way to get the
child class from that inherited main method so they have to do a bunch of
reflection.

- See line #457 of [CommandLineProgram.java](JavaTaskForce/src/acm/program/CommandLineProgram.java)
- [DOSCommandLine.java](JavaBackEnd/latest-version-decompiled/acm/util/DOSCommandLine.java)
