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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cca0ec0491d7a2c513f8bc52acaadf7c80d7fd22
ms.sourcegitcommit: 58000baf528da220fdf7a999d8c407a4e86c1278
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72789829"
---
# <a name="build-events-page-project-designer-c"></a>專案設計工具、建置事件 (C#)

使用 [專案設計工具] 的 [建置事件] 頁面，以指定組建組態指示。 您也可以指定執行任何建置後事件的條件。 如需詳細資訊，請參閱[如何：指定組建事件C#（）](../../ide/how-to-specify-build-events-csharp.md)和[如何：指定組建事件（Visual Basic）](../../ide/how-to-specify-build-events-visual-basic.md)。

## <a name="uielement-list"></a>UIElement 清單

**組態**

無法在此頁面中編輯這個控制項。 如需此控制項的描述，請參閱[專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)。

**平台**

在這個頁面上無法編輯此控制項。 如需此控制項的描述，請參閱[專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)。

**建置前事件命令列**

指定要在建置開始前執行的任何命令。 若要鍵入長命令，請按一下 [建置前進行編輯] 顯示[建置前事件/建置後事件命令列對話方塊](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。

> [!NOTE]
> 如果專案是最新狀態，而且未觸發任何建置，則建置前事件不會執行。

**建置後事件命令列**

指定要在建置結束後執行的任何命令。 若要鍵入長命令，請按一下 [建置後進行編輯] 顯示 [建置前事件/建置後事件命令列] 對話方塊。

> [!NOTE]
> 在執行 .bat 檔案的所有建置命令前方，加入 `call` 陳述式。 例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。

**執行建置後事件**

指定要執行建置後事件的下列條件，如下表所示。

|選項|結果|
|------------|------------|
|**永遠**|不論建置是否成功，都會執行建置後事件。|
|**建置成功時**|如果建置成功，則會執行建置後事件。 因此，即使專案是最新狀態，但只要建置成功，就會執行事件。|
|**當組建更新專案輸出時**|只有在編譯器的輸出檔 (.exe 或 .dll) 與先前的編譯器輸出檔不同時，才會執行建置後事件。 因此，如果專案是最新狀態，就不會執行建置後事件。|

## <a name="in-the-project-file"></a>在專案檔中

在舊版的 Visual Studio 中，當您在 IDE 中變更**PreBuildEvent**或**postbuildevent.bat**設定時，Visual Studio 會將 `PreBuildEvent` 或 `PostBuildEvent` 屬性加入至專案檔。 例如，如果您在 IDE 中的**PreBuildEvent**命令列設定如下：

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

然後，專案檔設定為：

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

Visual Studio 2019 （在較新的更新中 Visual Studio 2017）新增名為 `PreBuild` 的 MSBuild 目標，或**PreBuildEvent**和**postbuildevent.bat**設定的 `PostBuild`。 例如，在上述範例中，Visual Studio 現在會產生下列程式碼：

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

> [!NOTE]
> 已進行這些專案檔變更，以支援 SDK 樣式專案。 如果您以手動方式將專案檔從舊格式遷移至 SDK 樣式格式，您應該刪除 `PreBuildEvent` 並 `PostBuildEvent` 屬性，並以 `PreBuild` 和 `PostBuild` 目標取代，如上述程式碼所示。 若要瞭解如何判斷您的專案是否為 SDK 樣式的專案，請參閱[檢查項目格式](/nuget/resources/check-project-format)。

## <a name="see-also"></a>請參閱

- [如何：指定建置事件 (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [如何：指定建置事件 (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [專案屬性參考](../../ide/reference/project-properties-reference.md)
- [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)