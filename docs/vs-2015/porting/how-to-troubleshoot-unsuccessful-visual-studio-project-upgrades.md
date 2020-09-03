---
title: 如何：對不成功的專案升級進行疑難排解 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844442"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>如何：不成功的 Visual Studio 專案升級疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有時候 Visual Studio 無法從舊版的進行完整轉換專案 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 如果下列各節中的秘訣無法解決您的特定問題，您可能可以在 TechNet [Wiki：開發入口網站](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio)上找到詳細資訊。

## <a name="the-project-does-not-run-because-files-are-not-found"></a>因為找不到檔案，所以無法執行專案
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]當您按下 F5 時，專案檔包含用來執行專案的硬式編碼檔案路徑。 這些路徑可能包含 devenv.exe 和其他必要檔案的位置。 在升級版本的中 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，這些檔案的路徑可能已變更。

#### <a name="to-resolve-incorrect-file-paths"></a>解析不正確的檔案路徑

1. 在文字編輯器中開啟您的專案檔。

2. 掃描可能不正確的檔案路徑，特別是包含版本號碼的檔案路徑 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。

3. 修改不正確的檔案路徑，使其指向新的目標。

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>因為參考無效，所以無法建立專案
 升級時 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，您也可能會升級 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 如果您的專案包含在較新版本中停止的參考 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ，則可能無法正確解析。 這特別可能是包含版本號碼的參考，例如 `Microsoft.VisualStudio.Shell.Interop.8.0` 。

 如果您的程式碼有許多不正確參考，最簡單的解決方案可能是使用的多目標功能，將 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 目標設為舊版 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

#### <a name="to-resolve-incorrect-references"></a>若要解析不正確的參考

1. 在文字編輯器中開啟您的專案檔。

2. 開啟專案屬性。

3. 選取正確的 **目標 Framework** 值。 或者，您也可以 `<TargetFrameworkVersion>` 直接在專案檔中修改元素的值。

   如果您想要在升級的版本中執行專案 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ，您必須更新專案的參考，並同時更新任何 `Imports` `Using` 呼叫參考的或語句。 如果您的專案在 IDE 中載入，您可以使用 **方案總管** 或 [ **參考管理員** ] 對話方塊來更新參考。

## <a name="see-also"></a>另請參閱
 [/Upgrade ( # A0) ](../ide/reference/upgrade-devenv-exe.md) [轉換成 ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
