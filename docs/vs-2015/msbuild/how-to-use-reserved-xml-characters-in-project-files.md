---
title: 如何：在專案檔中使用保留的 XML 字元 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aba17e94486ca04e12055c7bf9959f927440c53d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178308"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>如何：在專案檔中使用保留的 XML 字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您撰寫專案檔時，您可能需要使用保留的 XML 字元，例如，在屬性值或工作參數值中。 不過，您必須使用具名實體來取代某些保留字元，如此才能剖析專案檔。  
  
## <a name="using-reserved-characters"></a>使用保留字元  
 下表說明您必須使用對應的具名實體來取代的保留 XML 字元，如此才能剖析專案檔。  
  
|保留字元|具名實體|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>在專案檔中使用雙引號  
  
- 使用對應的具名實體 &quot; 來取代雙引號。 例如，若要以雙引號括住 `EXEFile` 項目清單，請輸入：  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>範例  
 在下列程式碼範例中，於專案檔所輸出的訊息內，使用雙引號來反白顯示檔案名稱。  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 參考](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md)
