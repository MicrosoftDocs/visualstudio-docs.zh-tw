---
title: UWP 應用程式的應用程式屬性頁
description: 瞭解如何使用 [應用程式] 頁面來指定通用 Windows 平臺 (UWP) 專案的元件和套件資訊，並以 Windows 10 版本為目標。
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 21dd08f81802661cae9d77ee3449f4e9369ca768
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965079"
---
# <a name="application-property-page-uwp-projects"></a>應用程式屬性頁 (UWP 專案)

使用 [應用程式] 屬性頁指定通用 Windows 平台 (UWP) 專案的組件和套件資訊，並以 Windows 10 版本為目標。

![應用程式屬性頁](media/application-page-uwp.png)

若要存取 [應用程式] 頁面，請在 [方案總管] 中選擇專案節點。 然後選擇  >  功能表列上的 [專案 **屬性**]。 屬性頁會在 [應用程式] 索引標籤上開啟。

## <a name="general-section"></a>[一般] 區段

**元件名稱** &mdash;指定將保留組件資訊清單之輸出檔的名稱。

若要以程式設計方式存取此屬性，請參閱 <xref:VSLangProj.ProjectProperties.AssemblyName%2A>。

**預設命名空間** &mdash;指定新增至專案之檔案的基底命名空間。 如需命名空間的相關詳細資訊，請參閱[命名空間 (C# 程式設計手冊)](/dotnet/csharp/programming-guide/namespaces/)、[命名空間 (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)，或[命名空間 (C++)](/cpp/cpp/namespaces-cpp)。

若要以程式設計方式存取此屬性，請參閱 <xref:VSLangProj.ProjectProperties.RootNamespace%2A>。

**元件資訊** &mdash;選擇這個按鈕會顯示 [[元件資訊] 對話方塊](../../ide/reference/assembly-information-dialog-box.md)。

**封裝資訊清單** &mdash;選擇此按鈕會開啟資訊清單設計工具。 資訊清單設計工具可以透過選擇 [方案總管] 中的 _Package.appxmanifest_ 檔案加以存取。 如需詳細資訊，請參閱[使用資訊清單設計工具設定套件](/windows/msix/package/packaging-uwp-apps#configure-your-project)。

## <a name="targeting-section"></a>目標鎖定區段

您可以使用本區段中的下拉式清單，為您的應用程式設定 Windows 10 的目標版本和最低版本。 建議您以 Windows 10 最新版本為目標。如果您正在開發企業應用程式，則也應該支援較舊的最低版本。 如需選擇 Windows 10 版本的相關詳細資訊，請參閱[選擇 UWP 版本](/windows/uwp/updates-and-versions/choose-a-uwp-version)。

如需 Visual Studio 平台目標的資訊，請參閱[平台目標](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting)。

## <a name="see-also"></a>另請參閱

- [建立您的第一個 UWP 應用程式](/windows/uwp/get-started/your-first-app)
- [選擇 UWP 版本](/windows/uwp/updates-and-versions/choose-a-uwp-version)
