---
title: 建置動作
description: 本文描述各種可用於 C# 專案的建置動作
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714397"
---
# <a name="build-actions"></a>建置動作

Visual Studio for Mac 專案中的所有檔案都有一個建置動作。 生成操作控制生成期間檔發生的情況。 

>[!NOTE]
>本主題適用於 Visual Studio for Mac。 有關 Windows 上的視覺化工作室，請參閱[生成操作](/visualstudio/ide/build-actions)。

## <a name="set-a-build-action"></a>設定建置動作

要在 Mac 的 Visual Studio 中為檔設置生成操作，您可以按右鍵任何檔並流覽到**生成操作**，如下圖所示：

![從 [方案總管] 選取編譯建置動作](media/projects-and-solutions-image1.png)

此檔的生成操作將顯示在快顯視窗功能表中。 

## <a name="build-action-values"></a>建置動作值

在 Mac 視覺化工作室中構建專案的一些常見生成操作包括：

|建置動作 | 專案類型 | 描述 |
|--|--|--|
| **編譯** | 任意 | 該檔作為原始檔案傳遞給 C# 編譯器。|
| **內容** | .NET， 薩馬林 | 若是 ASP.NET 專案，這些檔案將在網站部署時納入為網站的一部分。 針對 Xamarin.iOS 和 Xamarin.Mac 專案，它們會包含在應用程式套件組合中。|
| **Embedded Resource** | .NET | 該檔作為要嵌入到程式集中的資源傳遞給 C# 編譯器。 之後，可以使用 `System.Reflection` 命名空間中的 [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream) 從組件中讀取該檔案。|
| **無** | 任意 | 該檔以任何方式不是生成中的一部分，並且包含在專案中，以便從 IDE 輕鬆訪問。 這個值可以用於文件檔，例如「讀我」檔案。|

> [!NOTE]
> 由於可以針對特定專案類型定義其他建置動作，因此建置動作清單會取決於專案類型，而且可能會出現不在此清單中的值。  

Xamarin.iOS 專案擁有 **BundleResource** 建置動作，該動作會新增檔案作為應用程式套件組合的一部分。 如需 Xamarin.Android 特定建置動作的資訊，請參閱[建置流程](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions)指南。

還可以在解決方案資源管理器中選擇多個檔，從而允許您一次將生成操作設置為多個檔。

## <a name="see-also"></a>另請參閱

- [建置動作 (Windows 上的 Visual Studio)](/visualstudio/ide/build-actions)