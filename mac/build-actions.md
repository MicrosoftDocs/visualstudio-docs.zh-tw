---
title: 建置動作
description: 本文描述各種可用於 C# 專案的建置動作
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 16617f8de15fbef40941c4f9409497da142c9e8a
ms.sourcegitcommit: f61ad0e8babec8810295f039e67629f4bdebeef0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2018
ms.locfileid: "52001174"
---
# <a name="build-actions"></a>建置動作

Visual Studio for Mac 專案中的所有檔案都有一個建置動作。 它可控制檔案在建置期間所發生的狀況。 這項行為可透過在任何檔案上按一下滑鼠右鍵，並瀏覽至 [建置動作] 進行設定，如下所示：

![從 [方案總管] 選取編譯建置動作](media/projects-and-solutions-image1.png)

一些 C# 專案的常見建置動作如下：

* **無** - 檔案在任何情況下都不是組建的一部分；它會包含在專案中以方便從 IDE 進行存取。
* **編譯** - 檔案將傳遞至 C# 編譯器作為來源檔案。
* **EmbeddedResource** - 檔案將傳遞至 C# 編譯器，作為要在組件中內嵌的資源。 之後，可以使用 `System.Reflection` 命名空間中的 [Assembly.GetManifestResourceStream](https://docs.microsoft.com/dotnet/api/system.reflection.assembly.getmanifestresourcestream) 從組件中讀取該檔案。
* **內容** - 若是 ASP.NET 專案，這些檔案將在網站部署時納入為網站的一部分。 針對 Xamarin.iOS 和 Xamarin.Mac 專案，它們會包含在應用程式套件組合中。

您可以在 [方案總管] 中選取多個檔案，這可讓您一次為多個檔案設定建置動作。

此外，還有針對特定專案的建置動作。 Xamarin.iOS 專案擁有 **BundleResource** 建置動作，該動作會新增檔案作為應用程式套件組合的一部分。 如需 Xamarin.Android 特定建置動作的資訊，請參閱[建置流程](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions)指南。

## <a name="see-also"></a>另請參閱

- [建置動作 (Windows 上的 Visual Studio)](/visualstudio/ide/build-actions)