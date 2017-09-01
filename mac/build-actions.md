---
title: "建置動作"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 347378da197b5c6d22bbd145c2ac8673d53a63bf
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---

# <a name="build-actions"></a>建置動作 

Visual Studio for Mac 專案中的所有檔案都有一個建置動作，用以控制檔案在建置期間所發生的狀況。 透過在任何檔案上按一下滑鼠右鍵，並瀏覽至 [建置動作] 即可進行設定，如下所示：

![](media/projects-and-solutions-image1.png)

一些 C# 專案的常見建置動作如下：

* **無** - 檔案在任何情況下都不是組建的一部分；它只會包含在專案中以方便從 IDE 進行存取。
* **編譯** - 檔案將傳遞至 C# 編譯器作為來源檔案。
* **EmbeddedResource** - 檔案將傳遞至 C# 編譯器，作為要在組件中內嵌的資源。 之後，可以使用 `System.Reflection` 命名空間從組件中讀取該檔案。
* **內容** - 若是 ASP.NET 專案，這些檔案將在網站部署時納入為網站的一部分。 若是 Xamarin.iOS 和 Xamarin.Mac 專案，它們會包含在應用程式套件組合中。

您可以在 [方案總管] 中選取多個檔案，這可讓您一次為多個檔案設定建置動作。

此外，還有針對特定專案的建置動作。 例如，Xamarin.iOS 專案擁有 **BundeledResource** 建置動作，該動作會新增檔案作為應用程式套件組合的一部分。 如需 Xamarin.Android 特定建置動作的資訊，請參閱 developer.xamarin.com 上的 [Build Process](https://developer.xamarin.com/guides/android/under_the_hood/build_process/#Build_Actions) (建置流程) 指南。
