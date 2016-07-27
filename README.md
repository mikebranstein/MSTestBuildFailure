# Overview
An example .NET solution to show how to execute MSTest after build, and fail the build step if the test run fails. The solution contains a single failing unit test, and thus when built, the build will fail.

# How to Use
Download the project, open the .sln file with Visual Studio. Build the solution. The build will compile the BuildFailure command line project, then the BuildFailure.Test project. 

## Verifying a Build Failure
When the BuildFailure.Test project is compiled, MSTest.exe will be invoked and execute the unit tests within the project. A single unit test exists, with an assert statement asserting that true is equal to false. Verify the build fails.

## Verifying a Build Success
Open the UnitTest1.cs file within the BuildFailure.Test project. Change the unit test to assert that true is equal to true. Rebuild the solution. The build will succeed.

# What's Going On?
This all happens within the BuildFailure.Test unit test project .csproj file. Open it up in a text editor and look for the comments labeled "Step 1" and "Step 2". 

The "Step 1" section establishes several variables used throughout the MS Build script. You can review these, but they're nothing special.

The "Step 2" section runs MS Test after the "build" portion of the script runs. If the output of the MS Test run fails, then the build reports a failure.

# Errata
I've tested this in Visual Studio 2015. If it doesn't work in other versions, let me know.

