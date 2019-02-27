---
title: 作法：在專案檔中使用保留的 XML 字元 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02c5693a2edca0d81e21e73215e00f25aae939eb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603863"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>作法：在專案檔中使用保留的 XML 字元
當您撰寫專案檔時，您可能需要使用保留的 XML 字元，例如，在屬性值或工作參數值中。 不過，您必須使用具名實體來取代某些保留字元，如此才能剖析專案檔。

## <a name="use-reserved-characters"></a>使用保留字元
 下表說明您必須使用對應的具名實體來取代的保留 XML 字元，如此才能剖析專案檔。

|保留字元|具名實體|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>在專案檔中使用雙引號

-   使用對應的具名實體 &amp;quot; 來取代雙引號。 例如，若要以雙引號括住 `EXEFile` 項目清單，請輸入：

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>範例
 在下列程式碼範例中，於專案檔所輸出的訊息內，使用雙引號來反白顯示檔案名稱。

```xml
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
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
