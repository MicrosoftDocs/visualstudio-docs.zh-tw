---
title: 如何：疑難排解不成功的專案升級 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 65059e285777e48633da5eb7e8723e3997f37dfa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844442"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>如何：不成功的 Visual Studio 專案升級疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有時候 Visual Studio 無法完全從舊版的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]轉換專案。 如果下列各節中的秘訣無法解決您的特定問題，您可能可以在 TechNet [Wiki：開發入口網站](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio)上找到詳細資訊。

## <a name="the-project-does-not-run-because-files-are-not-found"></a>因為找不到檔案，所以無法執行專案
 專案檔包含硬式編碼的檔案路徑，當您按下 F5 時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 用來執行專案。 這些路徑可能包括 devenv .exe 和其他必要檔案的位置。 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的升級版本中，這些檔案的路徑可能已變更。

#### <a name="to-resolve-incorrect-file-paths"></a>解析不正確的檔案路徑

1. 在文字編輯器中開啟您的專案檔。

2. 掃描可能不正確的檔案路徑，特別是包含 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 版本號碼的檔案路徑。

3. 修改不正確的檔案路徑，使其指向新的目標。

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>因為參考無效，所以無法建立專案
 當您升級 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]時，您可能也會升級 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 如果您的專案包含較新 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本中已停止的參考，則可能無法正確解析。 這特別可能用於包含版本號碼的參考，例如 `Microsoft.VisualStudio.Shell.Interop.8.0`。

 如果您的程式碼有許多不正確參考，最簡單的解決方案可能是使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的多目標功能，將目標設為舊版的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]。

#### <a name="to-resolve-incorrect-references"></a>解決不正確的參考

1. 在文字編輯器中開啟您的專案檔。

2. 開啟 [專案屬性]。

3. 選取正確的 [**目標 Framework** ] 值。 或者，您也可以直接在專案檔中修改 `<TargetFrameworkVersion>` 元素的值。

   如果您想要在升級的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本中執行專案，您必須更新專案的參考，同時更新呼叫參考的任何 `Imports` 或 `Using` 語句。 如果您的專案載入 IDE 中，您可以使用**方案總管**或 [**參考管理員**] 對話方塊來更新參考。

## <a name="see-also"></a>請參閱
 [/Upgrade （devenv .exe）](../ide/reference/upgrade-devenv-exe.md) [轉換成 ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
