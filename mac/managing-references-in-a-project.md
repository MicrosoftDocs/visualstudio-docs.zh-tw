---
title: "管理專案中的參考"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 30f6c99c6ac827b7da94fd228a7034e9ce0b0fac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="managing-references-in-a-project"></a>管理專案中的參考

Visual Studio for Mac 提供三種方式來新增專案的其他參考：

![專案參考](media/projects-and-solutions-image10.png)

這些是：

* 參考
* NuGets (透過 [套件] 資料夾新增)
* 元件

此外，Web 參考和原生參考也可以新增至任何專案。

## <a name="assembly-references"></a>組件參考

Xamarin 內的每個架構都會隨附許多組件。 根據預設，不會參考專案中的所有這些組件套件。 

若要編輯專案中所參考的套件，請使用 [編輯參考] 對話方塊，其顯示方法是按兩下 [參考] 資料夾，或在其操作功能表動作上選取 [編輯參考]：

![組件參考對話方塊](media/projects-and-solutions-image11.png)

如需每個 Xamarin 架構可用組件的資訊，請參閱 [Available Assemblies](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) (可用組件) 指南。

## <a name="nuget"></a>NuGet

NuGet 是適用於 .NET 開發最受歡迎的套件管理員。 Visual Studio for Mac 的 NuGet 支援可讓您搜尋要新增至專案的套件。

若要這樣做，請以滑鼠右鍵按一下 Solution Pad 中的 [套件] 資料夾，然後選取 [新增套件]。

如需使用 NuGet 套件的詳細資訊，請參閱[在專案中包含 NuGet 套件](~/nuget-walkthrough.md)逐步解說。
