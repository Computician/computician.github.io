---
layout: post
title: Package Management Console via the command line
---

### TL;DR
 [PMCCommand](https://github.com/Computician/PMCCommand) allows arbitrary Package Management Console commands against a solution or project from the command line.

## Accessing the Visual Studio PMC

The `Package Mangement Console` found in Visual Studio supplies some very useful commands that are not fully reflected in the nuget command line utility. A glaring example of this is `Update-Package`. When used inside the `Package Management Console` it will pull down and update any new dependencies referenced by the updated package. Conversely, [nuget update](https://docs.microsoft.com/en-us/nuget/tools/nuget-exe-cli-reference#update) will NOT do this.

> If an updated package has an added assembly, a new reference is not added. New package dependencies also don't have their assembly references added. To include these operations as part of an update, update the package in Visual Studio using the Package Manager UI or the Package Manager Console.

This is incredibly frustrating when trying to automate updates through a CI server. The Nuget maintainers are aware of this frustration but [actions have not been taken](https://github.com/NuGet/Home/issues/1512) and it does not appear that anything is going to be done very soon. So, I have written a tool that allows automation through Visual Studio (which is the currently suggested solution by the Nuget maintainers). [PMCCommand](https://github.com/Computician/PMCCommand) is a command line utility that allows arbitrary PMC commands to be made against a specified project or solution.


