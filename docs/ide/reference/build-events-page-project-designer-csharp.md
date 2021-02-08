---
title: 專案設計工具、建置事件 (C#)
description: 瞭解如何指定組建設定指示。 您也可以指定執行任何建置後事件的條件。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 51b430a18a3d0934c16de19cbde82177a5f21f12
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836458"
---
# <a name="build-events-page-project-designer-c"></a>專案設計工具、建置事件 (C#)

使用 [專案設計工具] 的 [建置事件] 頁面，以指定組建組態指示。 您也可以指定執行任何建置後事件的條件。 如需詳細資訊，請參閱 [如何：指定組建事件 (c # ) ](../../ide/how-to-specify-build-events-csharp.md) 和 [如何：指定組建事件 (Visual Basic) ](../../ide/how-to-specify-build-events-visual-basic.md)。

## <a name="uielement-list"></a>UIElement 清單

**Configuration**

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
|**Always**|不論建置是否成功，都會執行建置後事件。|
|**建置成功時**|如果建置成功，則會執行建置後事件。 因此，即使專案是最新狀態，但只要建置成功，就會執行事件。|
|**當組建更新專案輸出時**|只有在編譯器的輸出檔 (.exe 或 .dll) 與先前的編譯器輸出檔不同時，才會執行建置後事件。 因此，如果專案是最新狀態，就不會執行建置後事件。|

## <a name="in-the-project-file"></a>在專案檔中

在舊版 Visual Studio 中，當您變更 IDE 中的 **>prebuildevent.bat** 或 **PostBuildEvent** 設定時，Visual Studio 會將 `PreBuildEvent` 或屬性加入 `PostBuildEvent` 至專案檔。 舉例來說，如果您在 IDE 中的 **>prebuildevent.bat** 命令列設定如下：

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

專案檔案設定為：

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

針對 .NET Core 專案，Visual Studio 2019 (和 Visual Studio 2017 在較新的更新中) 加入名為 `PreBuild` 或的 MSBuild 目標， `PostBuild` 以 **>prebuildevent.bat** 和 **PostBuildEvent** 設定。 這些目標會使用 MSBuild 可辨識的 **BeforeTargets** 和 **AfterTargets** 屬性。 例如，在上述範例中，Visual Studio 現在會產生下列程式碼：

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

若為建立後事件，請使用名稱， `PostBuild` 並將屬性設定 `AfterTargets` 為 `PostBuildEvent` 。

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> 已進行這些專案檔變更，以支援 SDK 樣式專案。 如果您要以手動方式將專案檔從舊格式遷移至 SDK 樣式格式，您應該刪除 `PreBuildEvent` 和屬性， `PostBuildEvent` 並將其取代為 `PreBuild` 和 `PostBuild` 目標，如上述程式碼所示。 若要瞭解如何判斷您的專案是否為 SDK 樣式專案，請參閱 [檢查項目格式](/nuget/resources/check-project-format)。

## <a name="see-also"></a>另請參閱

- [如何：指定組建事件 (Visual Basic) ](../../ide/how-to-specify-build-events-visual-basic.md)
- [如何：指定組建事件 (c # ) ](../../ide/how-to-specify-build-events-csharp.md)
- [專案屬性參考](../../ide/reference/project-properties-reference.md)
- [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)
