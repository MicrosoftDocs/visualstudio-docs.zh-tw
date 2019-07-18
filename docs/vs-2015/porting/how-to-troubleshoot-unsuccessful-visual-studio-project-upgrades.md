---
title: 作法：不成功的專案升級疑難排解 |Microsoft Docs
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
ms.openlocfilehash: 1fe975fedb8237762d7dadffceff22203dcb899e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696384"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>HOW TO：不成功的 Visual Studio 專案升級疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有時候 Visual Studio 無法完全將專案從舊版的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 如果下列各節中的提示不會解決特定問題，您可以取得更多有關 TechNet [Wiki:開發入口網站](http://go.microsoft.com/fwlink/?LinkId=254808)。

## <a name="the-project-does-not-run-because-files-are-not-found"></a>專案不會執行，因為找不到檔案
 專案檔包含硬式編碼的檔案路徑，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]用來執行專案，當您按下 F5。 這些路徑可能包含 devenv.exe 和其他必要的檔案的位置。 中的升級版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，這些檔案的路徑可能已變更。

#### <a name="to-resolve-incorrect-file-paths"></a>若要解決不正確的檔案路徑

1. 在文字編輯器中開啟您的專案檔。

2. 掃描的檔案路徑可能不正確，尤其是那些包含[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]版本號碼。

3. 修改不正確的檔案路徑，使其指向新的目標。

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>專案未建置，因為參考無效
 當您升級[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，您可能也會升級[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]版本。 如果您的專案會包含已停用在較新的參考[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]版本中，它們可能無法正確解析。 這是特別的參考，例如，包含版本號碼可能`Microsoft.VisualStudio.Shell.Interop.8.0`。

 如果您的程式碼有許多無效的參考，若要使用的多目標功能，可能是最簡單的解決方案[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]為目標的舊版[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]。

#### <a name="to-resolve-incorrect-references"></a>若要解決不正確的參考

1. 在文字編輯器中開啟您的專案檔。

2. 開啟專案屬性。

3. 選取正確**目標 Framework**值。 或者，您可以修改的值`<TargetFrameworkVersion>`直接在專案檔中的項目。

   如果您要在升級中執行專案[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]版本中，您必須更新專案的參考，以及更新任何`Imports`或`Using`呼叫參考的陳述式。 如果您的專案載入在 IDE 中，您可以使用更新的參考**方案總管**或**參考管理員** 對話方塊。

## <a name="see-also"></a>另請參閱
 [/ 升級 (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [轉換至 ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
