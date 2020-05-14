---
title: 專案設計工具、建置事件 (C#)
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6629f41657a546ffb5fb48e0b6efb5f4f0dd50cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596875"
---
# <a name="build-events-page-project-designer-c"></a>專案設計工具、建置事件 (C#)

使用 [專案設計工具]**** 的 [建置事件]**** 頁面，以指定組建組態指示。 您也可以指定執行任何建置後事件的條件。 有關詳細資訊，請參閱[：指定建置事件 （C#）](../../ide/how-to-specify-build-events-csharp.md)以及如何[：指定建置事件（可視基本）。](../../ide/how-to-specify-build-events-visual-basic.md)

## <a name="uielement-list"></a>UIElement 清單

**組態**

無法在此頁面中編輯這個控制項。 如需此控制項的描述，請參閱[專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)。

**平台**

在這個頁面上無法編輯此控制項。 如需此控制項的描述，請參閱[專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)。

**建置前事件命令列**

指定要在建置開始前執行的任何命令。 若要鍵入長命令，請按一下 [建置前進行編輯]**** 顯示[建置前事件/建置後事件命令列對話方塊](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。

> [!NOTE]
> 如果專案是最新狀態，而且未觸發任何建置，則建置前事件不會執行。

**建置後事件命令列**

指定要在建置結束後執行的任何命令。 若要鍵入長命令，請按一下 [建置後進行編輯]**** 顯示 [建置前事件/建置後事件命令列]**** 對話方塊。

> [!NOTE]
> 在執行 .bat 檔案的所有建置命令前方，加入 `call` 陳述式。 例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。

**執行建置後事件**

指定要執行建置後事件的下列條件，如下表所示。

|選項|結果|
|------------|------------|
|**總是**|不論建置是否成功，都會執行建置後事件。|
|**建置成功時**|如果建置成功，則會執行建置後事件。 因此，即使專案是最新狀態，但只要建置成功，就會執行事件。|
|**當組建更新專案輸出時**|只有在編譯器的輸出檔 (.exe 或 .dll) 與先前的編譯器輸出檔不同時，才會執行建置後事件。 因此，如果專案是最新狀態，就不會執行建置後事件。|

## <a name="in-the-project-file"></a>在專案檔案中

在早期版本的 Visual Studio 中，當您更改 IDE 中的**PreBuildEvent**或**PostBuildEvent**設置`PreBuildEvent`時`PostBuildEvent`，Visual Studio 會向專案檔案添加 或 屬性。 例如，如果 IDE 中的**PreBuildEvent**命令列設置如下：

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

然後專案檔案設置是：

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

對於 .NET 核心專案，Visual Studio 2019（以及最近更新中的 Visual Studio 2017）`PreBuild`添加了`PostBuild`名為或用於**預構建事件**和**後構建事件**設置的 MSBuild 目標。 這些目標使用 MSBuild 識別的 **"前目標**"和 **"後目標"** 屬性。 例如，對於前面的示例，Visual Studio 現在生成以下代碼：

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

對於生成後事件，請使用名稱`PostBuild`並將屬性`AfterTargets`設置為`PostBuildEvent`。

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> 對這些專案檔案進行了更改，以支援 SDK 樣式的專案。 如果要手動將專案檔案從舊格式遷移到 SDK 樣式格式，則應刪除`PreBuildEvent`和`PostBuildEvent`屬性，並將其替換為`PreBuild`和`PostBuild`目標，如前面的代碼所示。 要瞭解如何判斷專案是否為 SDK 樣式的專案，請參閱[檢查項目格式](/nuget/resources/check-project-format)。

## <a name="see-also"></a>另請參閱

- [如何：指定建置事件（可視基本）](../../ide/how-to-specify-build-events-visual-basic.md)
- [如何：指定建置事件 （C#）](../../ide/how-to-specify-build-events-csharp.md)
- [專案屬性參考](../../ide/reference/project-properties-reference.md)
- [編譯和建造](../../ide/compiling-and-building-in-visual-studio.md)
