---
title: 多目標專案
description: 本檔提供如何在 Visual Studio for Mac 中設定多目標專案的總覽。
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451437"
---
# <a name="projects-with-multiple-target-frameworks"></a>具有多個目標 framework 的專案
在 Visual Studio for Mac 中，您可以將 Xamarin 或 .NET Core 專案設定為在數個 .NET Framework 版本的任何一個上執行，以及在數個系統平臺的任何一個上執行。 例如，您可以將專案的目標設為要在 .NET Framework 4.6 和 .NET Core 3.1 上執行。 

如需目標 Framework 的詳細資訊，請參閱[目標 Framework](/dotnet/standard/frameworks)。

> [!NOTE] 
> 本主題適用於 Visual Studio for Mac。 如需 Windows 上的 Visual Studio，請參閱[架構目標總覽](/visualstudio/ide/visual-studio-multi-targeting-overview)。

## <a name="targeting-multiple-frameworks"></a>以多個架構為目標

系統會在您的專案檔中指定目標 framework，您可以在專案上按一下滑鼠右鍵，然後選擇 [**工具] > [編輯**檔案] 命令來編輯。 當指定了單一目標架構時，請使用 TargetFramework 元素。 下列主控台應用程式專案檔案示範如何以 .NET Core 3.0 為目標：

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

深入瞭解如何以[多個](/dotnet/standard/frameworks#how-to-specify-target-frameworks)架構為目標。

## <a name="working-with-code-in-a-multi-target-project"></a>在多目標專案中使用程式碼
當您在具有多C#個目標 framework 的專案中編輯檔案時，可以指定要用來引導編輯器體驗的目標架構（例如，如果您使用該架構不支援的 API，則會顯示警告）。 您可以使用 [編輯器] 視窗左上角的 [**目標 framework** ] 選取器來變更目標 framework。

![使用目標 framework 選取器來變更目標 framework，位於編輯器視窗的頂端](media/project-multitargeting-framework-selector.png)

有時候，您需要根據應用程式的目標平臺來呼叫不同的 Api。 若要這樣做，您可以撰寫條件式程式碼來編譯器代碼以進行特定平臺：

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

撰寫程式碼時，您會在 IntelliSense 自動完成建議中看到警告，讓您知道應用程式支援的任何目標 framework 是否遺漏特定 Api。

![在 IntelliSense 中顯示的警告訊息，API 將無法用於指定的目標架構。 範例文字：命名空間 System.object、SharedUtils （netstandard 2.0）-無法使用。 您可以使用巡覽列來切換內容。](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>請參閱

- [架構目標總覽（Windows）](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [SDK 樣式專案中的目標 framework](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
