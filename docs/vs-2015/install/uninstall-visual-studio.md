---
title: 解除安裝 Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 81c01e96478ca83c546670897ab63e4eee64033f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777821"
---
# <a name="uninstall-visual-studio"></a>解除安裝 Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2017 最新文件，請參閱 <<c0> [ 解除安裝 Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/uninstall-visual-studio)。

此頁面會引導您完成解除安裝 Visual Studio 2015，較早版本的整合式開發人員的生產力工具套件。  
  
##  <a name="uninstalling"></a>   
#### <a name="to-uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>若要解除安裝 Visual Studio 使用 「 標準 」 解除安裝方法  
  
1. 在 **控制台中**上**程式和功能**頁面上，選取您想要解除安裝，然後選擇的產品版本**變更**。  
  
2. 在安裝精靈中，選擇**解除安裝**，選擇**是**，然後依照精靈中其餘的指示。  
  
   這個標準或預設方法會留下一些項目，您第一次安裝 Visual Studio 時最初安裝 （例如，Microsoft.NET Framework、 Microsoft Visual c + + 可轉散發套件、 Microsoft SQL Server 等）。   我們將保留安裝其他許多應用程式相依於這些因為這些項目。 不過，如果您想要太移除它們，選取 在其項目**程式和功能**，然後個別移除每個。  
  
#### <a name="to-uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>若要解除安裝 Visual Studio 和所有其他相關的檔案 (亦即，若要解除安裝幾乎所有項目)  
  
1.  找出 Visual Studio.exe 檔案 （例如，尋找"vs_enterprise.exe"）。  
  
    > [!NOTE]
    >  檔案應該位於"%ProgramData%\Package 快取 」 的子資料夾，例如： C:\ProgramData\Package 快取\\{37e19555-e88d-4aed-9d42-82d0784d2b79} \vs_enterprise.exe  
  
2.  執行此.exe 檔案使用 /uninstall /force 命令列參數。  
  
     例如，執行```vs_enterprise.exe /uninstall /force```，這會移除 Visual Studio 和大部分的核心元件留下中預設解除安裝。 不過，它將不會移除所有其他內容，Visual Studio 附加元件和延伸模組可以安裝 （例如 Visual Studio 更新和其他選用元件）。  
  
    > [!TIP]
    > 或者，您可以使用 「**完整解除安裝程式**」 移除所有項目的 Visual Studio 工具，或可能已安裝 Visual Studio 更新。 也就是任何版本的 Visual Studio 2013 或更新版本。 若要深入了解，請參閱[Visual Studio 解除安裝工具](https://github.com/Microsoft/VisualStudioUninstaller/releases)GitHub 上。  
  
#### <a name="to-uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>若要以無訊息或被動模式解除安裝 Visual Studio (亦即從來源解除安裝)  
  
1.  在安裝 Visual Studio 的電腦上，開啟 Windows 命令提示字元。  
  
2.  輸入下列參數：  
  
     *DVDRoot* \\< 安裝檔案\> \</quiet/&#124;/被動 > [/norestart] /uninstall  
  
#### <a name="to-roll-back-to-a-previous-version-or-release-of--visual-studio"></a>若要回復成先前的版本或版本的 Visual Studio  
  
1. 使用本主題中所列的方法之一，解除安裝 Visual Studio。  
  
   > [!WARNING]
   >  解除安裝目前版本的 Visual Studio （或 Visual Studio Update），然後安裝 先前的版本中可能無法正常運作。  
   >   
   >  結果取決於其版本或版本的 Visual Studio 您已安裝，安裝的一個元件的版本，已安裝哪些產品可能會有相依性可能是與 Visual Studio 版本或元件，以及最後，在想要安裝或重新安裝舊版 Visual Studio 版本。  由於所有這些變數，標準解除安裝將會經常離開元件可能無法使用舊版 Visual Studio 版本或版本。  
   >   
   >  因此，為了獲得最佳結果，我們建議您使用[Visual Studio 解除安裝工具](https://github.com/Microsoft/VisualStudioUninstaller/releases)。  
  
2. 安裝或重新安裝您想要使用的 Visual Studio 舊版。  
  
   即使您安裝舊版的 Visual Studio，安裝程式可能仍然嘗試使用較新版本或版本，如果有的話。 如需詳細資訊，請參閱 <<c0> [ 如何： 安裝特定版本的 Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)主題。  
  
## <a name="see-also"></a>另請參閱  
 [安裝 Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)