---
title: 解除安裝 Visual Studio
titleSuffix: ''
description: 了解如何逐步解除安裝 Visual Studio。
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7d7c4400d553d8244d3b9239f0b0a984d382c99a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959164"
---
# <a name="uninstall-visual-studio"></a>解除安裝 Visual Studio

Visual Studio 是我們提供給開發人員的整合式生產力工具套件，本頁面將引導您完成 Visual Studio 的解除安裝作業。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[解除安裝 Visual Studio for Mac](/visualstudio/mac/uninstall)。

> [!TIP]
> 如果您的 Visual Studio 實例遇到問題，請嘗試 **修復** 工具。 如需詳細資訊，請參閱 [修復 Visual Studio](../install/repair-visual-studio.md)。 
>
> 如果您想要變更某些 Visual Studio 檔案的位置，則可以這麼做，而不需要卸載目前的實例。 如需詳細資訊，請參閱 [Visual Studio 中的選取安裝位置](../install/change-installation-locations.md)。
>
> 如需一般疑難排解秘訣，請參閱 [疑難排解 Visual Studio 安裝和升級問題](../install/troubleshooting-installation-issues.md)。

::: moniker range="vs-2017"

1. 在電腦上找到 Visual Studio 安裝程式。

     例如，在執行「Windows 10 年度更新版」或更新版本的電腦上，選取 [開始]，然後捲動至字母 [V]，它會列為 [Visual Studio 安裝程式]。

     ![Visual Studio 安裝程式](media/locate-the-visual-studio-installer.png "找出 Microsoft Visual Studio 安裝程式")

   > [!NOTE]
   > 在某些電腦上，Visual Studio 安裝程式可能會列在 **"M"** 字母下方，成為 [Microsoft Visual Studio 安裝程式]。<br/><br/> 您也可以在下列位置找到 Visual Studio 安裝程式：`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. 請在安裝程式中尋找您安裝的 Visual Studio 版本。 接著，選擇 [更多]，然後選擇 [解除安裝]。

     ![解除安裝 Visual Studio 2017](media/uninstall-visual-studio.png "解除安裝 Visual Studio 2017")

1. 按一下 [確定] 確認您的選擇。

如果您稍後改變心意而想要重新安裝 Visual Studio 2017，請重新啟動 Visual Studio 安裝程式，然後從選擇畫面中選取 [安裝]。

## <a name="uninstall-visual-studio-installer"></a>解除安裝 Visual Studio 安裝程式

若要從您的機器中完全移除 Visual Studio 2017 的所有安裝和 Visual Studio 安裝程式，請從 [應用程式與功能] 來解除安裝。

1. 在 Windows 10 中，於 [在這裡輸入要搜尋的文字] 方塊中鍵入 **應用程式和功能**。
1. 尋找 **Microsoft Visual Studio 2017** (或稱 **Visual Studio 2017**)。
1. 選擇 **解除安裝**。
1. 然後，尋找 **Microsoft Visual Studio 安裝程式**。
1. 選擇 **解除安裝**。

::: moniker-end

::: moniker range="vs-2019"

1. 在您的電腦上找到 **Visual Studio 安裝程式**。

     在 Windows [開始] 功能表中，您可搜尋「安裝程式」。

     ![Visual Studio 安裝程式](media/vs-2019/visual-studio-installer.png "搜尋 Visual Studio 安裝程式")

     > [!NOTE]
     > 您也可以在下列位置找到 Visual Studio 安裝程式：
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    您可能需要更新安裝程式才能繼續。 若是如此，請遵循提示。

1. 請在安裝程式中尋找您安裝的 Visual Studio 版本。 接著，選擇 [更多]，然後選擇 [解除安裝]。

     ![卸載 Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "卸載 Visual Studio 2019")

1. 按一下 [確定] 確認您的選擇。

     ![卸載 Visual Studio 確認](media/vs-2019/uninstall-visualstudio-confirm.png "確認您想要卸載 Visual Studio 2019")

如果稍後改變心意並想要重新安裝 Visual Studio 2019，請再次啟動 Visual Studio 安裝程式，選擇 [可用] 索引標籤，選擇您想要安裝的 Visual Studio 版本，然後選取 [安裝]。

## <a name="uninstall-visual-studio-installer"></a>解除安裝 Visual Studio 安裝程式

若要從您的機器中完全移除 Visual Studio 2019 的所有安裝和 Visual Studio 安裝程式，請從 [應用程式與功能] 來解除安裝。

1. 在 Windows 10 中，於 [在這裡輸入要搜尋的文字] 方塊中鍵入 **應用程式和功能**。
1. 尋找 **Visual Studio 2019**。
1. 選擇 **解除安裝**。
1. 然後，尋找 **Microsoft Visual Studio 安裝程式**。
1. 選擇 **解除安裝**。

::: moniker-end

## <a name="remove-all-files"></a>移除所有檔案

如果您遇到重大錯誤，且無法使用先前的指示卸載 Visual Studio，則可以改為考慮使用「最後手段」選項。 如需有關如何完全移除所有 Visual Studio 安裝檔案和產品資訊的詳細資訊，請參閱 [移除 Visual Studio](remove-visual-studio.md) 頁面。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [修改 Visual Studio 2017](modify-visual-studio.md)
* [更新 Visual Studio 2017](update-visual-studio.md)
