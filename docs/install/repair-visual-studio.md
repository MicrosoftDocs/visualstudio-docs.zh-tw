---
title: 修復 Visual Studio
titleSuffix: ''
description: 了解如何修復 Visual Studio 2017 的安裝
ms.date: 10/12/2020
ms.custom: vs-acquisition
ms.topic: how-to
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 55ebb7c44b44a14154cc54f54885455821f9ee68
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386783"
---
# <a name="repair-visual-studio"></a>修復 Visual Studio

有時您的 Visual Studio 安裝會損壞或損毀。 修復對於修正所有安裝作業（包括更新）的安裝時間問題很有用。

## <a name="when-to-use-repair"></a>使用修復的時機
* 如果您遇到安裝承載問題。 將檔案寫入磁片時可能會發生這種情況，無法藉由刪除損毀的檔案來修正。 修復可以重新取得需要的檔案。 
* 如果您遇到用戶端下載問題。 假設您已解決任何連線或 proxy 問題，修復可能會有所説明。 
* 如果您在更新 Visual Studio 時發生問題。 修復修正許多常見的更新問題。 

> [!TIP] 
> 如果安裝問題是因為基礎 Windows 服務的問題所造成，例如 Windows Installer，修復可能會遇到相同的問題。 系統性問題可能包括中斷的 Windows Installer 或不穩定的網際網路連線。 若要檢查是否有系統問題，請使用安裝作業所產生的錯誤報表。

> [!NOTE] 
> 修復 Visual Studio 會重設使用者設定，並重新安裝已有的元件。 如果您遇到產品問題，請建立 [Visual Studio 意見反應票證](https://aka.ms/feedback/suggest?space=8)，因為 repair 可能無法解決此問題。

## <a name="how-to-repair"></a>如何修復
::: moniker range="vs-2017"

1. 在您的電腦上找到 **Visual Studio 安裝程式**。

     例如，在執行「Windows 10 年度更新版」或更新版本的電腦上，選取 [開始]，然後捲動至字母 [V]，它是列為 [Visual Studio 安裝程式]。

   > [!NOTE]
   > 在某些電腦上，Visual Studio 安裝程式可能會列在 **"M"** 字母下方，成為 [Microsoft Visual Studio 安裝程式]。
   >
   > 您也可以在下列位置找到 Visual Studio 安裝程式：`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. 開啟安裝程式，選擇 [更多]，然後選擇 [修復]。

    ![從 Visual Studio 安裝程式修復 Visual Studio](media/repair-visual-studio.png "從 Visual Studio 安裝程式修復 Visual Studio")

   > [!NOTE]
   > 修復 Visual Studio 會重設環境。 個別使用者沒有使用提高權限所安裝的擴充、使用者設定和設定檔等本機自訂項目會被移除。 佈景主題、色彩、按鍵繫結等已同步處理的設定會還原。
   >

   > [!TIP]
   > [修復] 選項僅會針對已安裝的 Visual Studio 執行個體加以顯示。 如果您看不到 [修復] 選項，很可能是您選取 [更多] 的版本在 Visual Studio 安裝程式中是列為「可用」而非「已安裝」。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在您的電腦上找到 **Visual Studio 安裝程式**。

     在 Windows [開始] 功能表中，您可搜尋「安裝程式」。

     ![Visual Studio 安裝程式](media/vs-2019/visual-studio-installer.png "搜尋 Visual Studio 安裝程式")

     > [!NOTE]
     > 您也可以在下列位置找到 Visual Studio 安裝程式：
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    您可能需要更新安裝程式才能繼續。 若是如此，請遵循提示。

1. 請在安裝程式中尋找您安裝的 Visual Studio 版本。 接著，選擇 [更多]，然後選擇 [修復]。

     ![修復 Visual Studio 2019](media/vs-2019/vs-installer-repair.png "修復 Visual Studio 2019")

   > [!NOTE]
   > 修復 Visual Studio 會重設環境。 個別使用者沒有使用提高權限所安裝的擴充、使用者設定和設定檔等本機自訂項目會被移除。 佈景主題、色彩、按鍵繫結等已同步處理的設定會還原。
   >

   > [!TIP]
   > [修復] 選項僅會針對已安裝的 Visual Studio 執行個體加以顯示。 如果您看不到 [修復] 選項，很可能是您選取 [更多] 的版本在 Visual Studio 安裝程式中是列為「可用」而非「已安裝」。

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [更新 Visual Studio 2017](update-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
* [針對 Visual Studio 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)
