---
title: 建置前事件/建置後事件命令列對話方塊 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b42c219620a669a8fa27a7ce847dc571a4075288
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662172"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>建置前事件/建置後事件命令列對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以直接在編輯方塊中鍵入[專案設計工具、建置事件頁面 (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)的建置前或建置後事件，或者可以從可用的巨集清單選取建置前或建置後巨集。

> [!NOTE]
> 如果專案是最新狀態，而且未觸發任何建置，則建置前事件不會執行。

## <a name="ui-element-list"></a>UI 項目清單
 **命令列編輯方塊** 包含要針對預先建立或之後組建執行的事件。

> [!NOTE]
> 在執行 .bat 檔案的所有建置命令前方，加入 `call` 陳述式。 例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。

 **宏** 展開編輯方塊以顯示要插入命令列編輯方塊中的宏清單。

 **宏資料表** 列出可用的宏和其值。 每個巨集的描述，請參閱底下的＜巨集＞。 您可以一次只選取一個巨集來插入命令列編輯方塊中。

 **插入** 在命令列編輯方塊中插入宏資料表中選取的宏。

### <a name="macros"></a>巨集
 您可以使用任何這些巨集指定檔案位置，或是在複選的情況下取得輸入檔的實際名稱。 這些巨集不區分大小寫。

|巨集|描述|
|-----------|-----------------|
|`$(ConfigurationName)`|目前的專案設定名稱，例如 "Debug"。|
|`$(OutDir)`|相對於專案目錄的輸出檔目錄路徑。 這會解析為 Output Directory 屬性的值。 它包含尾端的反斜線 '\\'。|
|`$(DevEnvDir)`|Visual Studio 的安裝目錄 (定義為磁碟機和路徑)，尾端有反斜線 '\\'。|
|`$(PlatformName)`|目前目標平台的名稱。 例如 "AnyCPU"。|
|`$(ProjectDir)`|專案的目錄 (定義為磁碟機和路徑)，尾端有反斜線 '\\'。|
|`$(ProjectPath)`|專案的絕對路徑名稱 (定義為磁碟機、路徑、主檔名和副檔名)。|
|`$(ProjectName)`|專案的主檔名。|
|`$(ProjectFileName)`|專案的檔案名稱 (定義為主檔名和副檔名)。|
|`$(ProjectExt)`|專案的副檔名。 副檔名前面有 '.'。|
|`$(SolutionDir)`|解決方案的目錄 (定義為磁碟機和路徑)，尾端有反斜線 '\\'。|
|`$(SolutionPath)`|解決方案的絕對路徑名稱 (定義為磁碟機、路徑、主檔名和副檔名)。|
|`$(SolutionName)`|解決方案的主檔名。|
|`$(SolutionFileName)`|解決方案的檔案名稱 (定義為主檔名和副檔名)。|
|`$(SolutionExt)`|解決方案的副檔名。 副檔名前面有 '.'。|
|`$(TargetDir)`|組建的主要輸出檔目錄 (定義為磁碟機和路徑)。 它包含尾端的反斜線 '\\'。|
|`$(TargetPath)`|組建的主要輸出檔絕對路徑名稱 (定義為磁碟機、路徑、主檔名和副檔名)。|
|`$(TargetName)`|建置的主要輸出檔主檔名。|
|`$(TargetFileName)`|組建的主要輸出檔檔案名稱 (定義為主檔名和副檔名)。|
|`$(TargetExt)`|建置的主要輸出檔副檔名。 副檔名前面有 '.'。|

## <a name="see-also"></a>另請參閱
 在 Visual Studio [Build events （專案設計工具）頁面](../../ide/reference/build-events-page-project-designer-csharp.md)[中指定自訂群組建事件](../../ide/specifying-custom-build-events-in-visual-studio.md) (c # ) [如何：指定組建事件 (Visual Basic) ](../../ide/how-to-specify-build-events-visual-basic.md) [如何：指定組建事件 (c # ) ](../../ide/how-to-specify-build-events-csharp.md)
