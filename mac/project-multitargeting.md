---
title: 多目標專案
description: 本檔概述如何在 Visual Studio for Mac 中設定多目標專案。
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451437"
---
# <a name="projects-with-multiple-target-frameworks"></a>具有多個目標 framework 的專案
在 Visual Studio for Mac 中，您可以將 Xamarin 或 .NET Core 專案設定為在數個 .NET Framework 版本的任何一個上執行，並在數個系統平臺的任何一個上執行。 例如，您可以將專案的目標設為在 .NET Framework 4.6 和 .NET Core 3.1 上執行。 

如需目標 Framework 的詳細資訊，請參閱[目標 Framework](/dotnet/standard/frameworks)。

> [!NOTE] 
> 本主題適用於 Visual Studio for Mac。 針對 Windows 上的 Visual Studio，請參閱 [架構目標總覽](/visualstudio/ide/visual-studio-multi-targeting-overview)。

## <a name="targeting-multiple-frameworks"></a>以多個 framework 為目標

目標 framework 是在您的專案檔中指定的，您可以在專案上按一下滑鼠右鍵，然後選擇 [ **工具] > 編輯** 檔案] 命令來進行編輯。 指定單一目標 Framework 時，請使用 TargetFramework 項目。 下列主控台應用程式專案檔會示範如何將目標設為 .NET Core 3.0：

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

使用具有多個目標 framework 的複數 TargetFrameworks 元素：

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

深入瞭解如何以 [多個](/dotnet/standard/frameworks#how-to-specify-target-frameworks)架構為目標。

## <a name="working-with-code-in-a-multi-target-project"></a>使用多目標專案中的程式碼
當您在具有多個目標 framework 的專案中編輯 c # 檔案時，可以指定您想要使用的目標 framework 來引導您的編輯器體驗 (例如，如果您使用的是該 framework) 不支援的 API，則會顯示警告。 您可以使用 [編輯器] 視窗左上角的 [ **目標 framework** 選取器] 來變更目標 framework。

![使用目標 framework 選取器來變更目標 framework （位於編輯器視窗頂端）](media/project-multitargeting-framework-selector.png)

有時您需要根據應用程式的目標平臺來呼叫不同的 Api。 若要這樣做，您可以撰寫條件式程式碼來編譯特定平臺的程式碼：

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

撰寫程式碼時，您會在 IntelliSense 自動完成建議中看到警告，讓您知道應用程式所支援的任何目標 framework 是否遺漏特定 Api。

![IntelliSense 中顯示的警告訊息，API 將無法用於指定的目標架構。 範例文字： namespace System. 緩衝區、SharedUtils (netstandard 2.0) -無法使用。 您可以使用巡覽列來切換內容。](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>另請參閱

- [架構目標總覽 (Windows) ](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [SDK 樣式專案中的目標 framework](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
