---
title: 解除安裝 Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ed9d33501644c6fa7252dffa758f92c0919653b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546898"
---
# <a name="uninstall-visual-studio"></a>解除安裝 Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新文件，請參閱[將 Visual Studio 解除安裝](/visualstudio/install/uninstall-visual-studio)。

Visual Studio 2015 是我們提供給開發人員的整合式生產力工具套件早期版本，此頁面將引導您完成 Visual Studio 2015 的解除安裝作業。

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>使用「標準」解除安裝方法將 Visual Studio 解除安裝

1. 在 [控制台]**** 的 [程式和功能]**** 頁面上，選取要解除安裝的產品版本，然後選擇 [變更]****。

2. 在 [安裝精靈] 中，依序選擇 [解除安裝]****、[是]****，然後遵循精靈中的其餘指示進行。

   此標準或預設方法會留下一些您第一次執行 Visual Studio 原始安裝所安裝的項目 (例如，Microsoft .NET Framework、Microsoft Visual C++ 可轉散發套件、Microsoft SQL Server 等)。   因為許多其他應用程式相依於這些項目，所以我們保留它們。 不過，如果您也想要移除它們，請在 [程式和功能]**** 中選取其項目，然後個別移除每個項目。

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>將 Visual Studio 和所有其他相關檔案解除安裝 (亦即，將幾乎所有項目都解除安裝)

1. 找出 Visual Studio.exe 檔案 (例如，尋找 "vs_enterprise.exe")。

    > [!NOTE]
    > 該檔案應該位在 "%ProgramData%\Package Cache" 的子資料夾中，例如：C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79}\vs_enterprise.exe

2. 使用 /uninstall /force 命令列參數來執行該 .exe 檔案。

     例如，執行 ```vs_enterprise.exe /uninstall /force``` 會將 Visual Studio 和預設解除安裝留下的大部分核心元件都移除。 不過，它不會移除 Visual Studio 增益集和擴充功能可安裝的所有額外內容 (例如，Visual Studio 更新和其他選用元件)。

    > [!TIP]
    > 或者，您可以使用「**完整解除安裝程式**」工具來移除 Visual Studio 或 Visual Studio 更新可能已安裝的所有項目。 也就是 Visual Studio 2013 或更新的任何版本。 若要深入了解，請參閱 GitHub 上的 [Visual Studio 解除安裝程式工具](https://github.com/Microsoft/VisualStudioUninstaller/releases) \(英文\)。

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>以無訊息或被動模式將 Visual Studio 解除安裝 (亦即從來源解除安裝)

1. 在安裝 Visual Studio 的電腦上，開啟 Windows 命令提示字元。

2. 輸入下列參數：

     *DVDRoot* \\<安裝檔案 \> \</quiet&#124;/passive> [/norestart]/uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>復原為 Visual Studio 的先前版本或版次

1. 使用此主題中所列的任何方法來將 Visual Studio 解除安裝。

   > [!WARNING]
   > 將 Visual Studio 的目前版次 (或 Visual Studio Update) 解除安裝，然後安裝先前版次，可能不會如預期般運作。
   >
   > 您安裝的 Visual Studio 版本或版次、所安裝元件的版本、所安裝可能有 Visual Studio 版次或其元件相依性的產品，以及您要安裝或重新安裝的先前 Visual Studio 版本，都會影響結果。  因為全部這些變數，所以標準解除安裝通常會留下元件，而先前的 Visual Studio 版本或版次可能無法使用這些元件。
   >
   > 因此，為了獲得最佳結果，我們建議您使用 [Visual Studio 解除安裝工具](https://github.com/Microsoft/VisualStudioUninstaller/releases) \(英文\)。

2. 安裝或重新安裝您想要使用的 Visual Studio 先前版本。

   即使您安裝 Visual Studio 的先前版本，安裝程式可能仍嘗試使用可取得的較新版本或版次。 如需詳細資訊，請參閱[如何：安裝特定版本的 Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md) 主題。

## <a name="see-also"></a>另請參閱

- [安裝 Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)