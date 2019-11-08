---
title: 建置動作
description: 本文描述各種可用於 C# 專案的建置動作
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714397"
---
# <a name="build-actions"></a>建置動作

Visual Studio for Mac 專案中的所有檔案都有一個建置動作。 [組建] 動作可控制在組建期間，檔案會發生什麼事。 

>[!NOTE]
>本主題適用於 Visual Studio for Mac。 如需 Windows 上的 Visual Studio，請參閱[組建動作](/visualstudio/ide/build-actions)。

## <a name="set-a-build-action"></a>設定建置動作

若要在 Visual Studio for Mac 中設定檔案的組建動作，您可以在任何檔案上按一下滑鼠右鍵，然後流覽至 [**建立] 動作**，如下所示：

![從 [方案總管] 選取編譯建置動作](media/projects-and-solutions-image1.png)

這個檔案的組建動作會顯示在 [飛出視窗] 功能表中。 

## <a name="build-action-values"></a>建置動作值

您可以在 Visual Studio for Mac 中建立之專案的一些常見組建動作包括：

|建置動作 | 專案類型 | 描述 |
|--|--|--|
| **Compile** | 任何 | 檔案會以原始檔的C#形式傳遞給編譯器。|
| **Content** | .NET、Xamarin | 若是 ASP.NET 專案，這些檔案將在網站部署時納入為網站的一部分。 針對 Xamarin.iOS 和 Xamarin.Mac 專案，它們會包含在應用程式套件組合中。|
| **Embedded Resource** | .NET | 檔案會以資源的形式C#傳遞給編譯器，以內嵌在元件中。 之後，可以使用 `System.Reflection` 命名空間中的 [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream) 從組件中讀取該檔案。|
| **無** | 任何 | 檔案不是組建的一部分，而且會包含在專案中，以便從 IDE 輕鬆存取。 這個值可以用於文件檔，例如「讀我」檔案。|

> [!NOTE]
> 由於可以針對特定專案類型定義其他建置動作，因此建置動作清單會取決於專案類型，而且可能會出現不在此清單中的值。  

Xamarin.iOS 專案擁有 **BundleResource** 建置動作，該動作會新增檔案作為應用程式套件組合的一部分。 如需 Xamarin.Android 特定建置動作的資訊，請參閱[建置流程](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions)指南。

您也可以在 [方案瀏覽器] 中選取一個以上的檔案，讓您一次將組建動作設定為多個檔案。

## <a name="see-also"></a>請參閱

- [建置動作 (Windows 上的 Visual Studio)](/visualstudio/ide/build-actions)