---
title: 多目標專案
description: 本文檔概述了如何在 Mac 視覺化工作室中設置多目標專案。
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451437"
---
# <a name="projects-with-multiple-target-frameworks"></a>具有多個目標框架的專案
在適用于 Mac 的 Visual Studio 中，您可以將 Xamarin 或 .NET Core 專案配置為在 .NET 框架的多個版本之一和多個系統平臺中的任何一個上運行。 例如，您可以將專案定位為在 .NET 框架 4.6 和 .NET Core 3.1 上運行。 

如需目標 Framework 的詳細資訊，請參閱[目標 Framework](/dotnet/standard/frameworks)。

> [!NOTE] 
> 本主題適用於 Visual Studio for Mac。 有關 Windows 上的視覺化工作室，請參閱[框架定位概述](/visualstudio/ide/visual-studio-multi-targeting-overview)。

## <a name="targeting-multiple-frameworks"></a>瞄準多個框架

目標框架在專案檔案中指定，您可以通過按右鍵專案並選擇 **"工具>編輯檔**"命令進行編輯。 指定單一目標 Framework 時，請使用 TargetFramework 項目。 以下主控台應用專案檔案演示如何定位 .NET Core 3.0：

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

將多數目標框架元素與多個目標框架一起使用：

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

詳細瞭解如何[定位多個框架](/dotnet/standard/frameworks#how-to-specify-target-frameworks)。

## <a name="working-with-code-in-a-multi-target-project"></a>在多目標專案中處理代碼
在具有多個目標框架的專案中編輯 C# 檔時，可以指定要使用哪個目標框架來指導編輯器體驗（例如，如果使用該框架不支援的 API，則顯示警告）。 您可以使用編輯器視窗左上角**的目標框架**選擇器更改目標框架。

![使用目標框架選擇器更改位於編輯器視窗頂部的目標框架](media/project-multitargeting-framework-selector.png)

有時，您需要根據應用程式所定位的平台叫用不同的 API。 為此，可以編寫條件碼來編譯特定平臺的代碼：

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

編寫代碼時，您將在 IntelliSense 自動完成建議中看到警告，讓您知道應用程式支援的任何目標框架是否缺少特定的 API。

![IntelliSense 中顯示的警告訊息，API 不適用於指定的目標框架。 示例文本：命名空間系統.緩衝區，共用 Utils （net標準2.0） - 不可用。 您可以使用巡覽列切換上下文。](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>另請參閱

- [框架目標概述（視窗）](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [SDK 樣式專案中的目標框架](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
