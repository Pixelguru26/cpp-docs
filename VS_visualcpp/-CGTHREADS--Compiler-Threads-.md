---
title: "-CGTHREADS (Compiler Threads)"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
H1: /CGTHREADS (Compiler Threads)
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
caps.latest.revision: 5
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# -CGTHREADS (Compiler Threads)
Sets the number of cl.exe threads to use for optimization and code generation when link-time code generation is specified.  
  
## Syntax  
  
```  
/CGTHREADS:[1-8]  
```  
  
## Arguments  
 number  
 The maximum number of threads for cl.exe to use, in the range 1 to 8.  
  
## Remarks  
 The **/CGTHREADS** option specifies the maximum number of threads cl.exe uses in parallel for the optimization and code-generation phases of compilation when link-time code generation ([/LTCG](../VS_visualcpp/-LTCG--Link-time-Code-Generation-.md)) is specified. By default, cl.exe uses four threads, as if **/CGTHREADS:4** were specified. If more processor cores are available, a larger `number` value can improve build times.  
  
 Multiple levels of parallelism can be specified for a build. The msbuild.exe switch **/maxcpucount** specifies the number of MSBuild processes that can be run in parallel. The [/MP (Build with Multiple Processes)](../VS_visualcpp/-MP--Build-with-Multiple-Processes-.md) compiler flag specifies the number of cl.exe processes that simultaneously compile the source files. The [/cgthreads](../VS_visualcpp/-cgthreads--Code-Generation-Threads-.md) compiler option specifies the number of threads used by each cl.exe process. Because the processor can only run as many threads at the same time as there are processor cores, it's not useful to specify larger values for all of these options at the same time, and it can be counterproductive. For more information about how to build projects in parallel, see [Building Multiple Projects in Parallel](../Topic/Building%20Multiple%20Projects%20in%20Parallel%20with%20MSBuild.md).  
  
### To set this linker option in the Visual Studio development environment  
  
1.  Open the project's **Property Pages** dialog box. For details, see [Working with Project Properties](../VS_visualcpp/Working-with-Project-Properties.md).  
  
2.  Select the **Configuration Properties**, **Linker** folder.  
  
3.  Select the **Command Line** property page.  
  
4.  Modify the **Additional Options** property to include **/CGTHREADS:**`number`, where `number` is a value from 1 to 8, and then choose **OK**.  
  
### To set this linker option programmatically  
  
-   See <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions?qualifyHint=False>.  
  
## See Also  
 [Linker Options](../VS_visualcpp/Linker-Options.md)   
 [Setting Linker Options](../VS_visualcpp/Setting-Linker-Options.md)