---
title: 開發最佳作法： Office 中的 COM、VSTO、& 的 VBA 增益集
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24cc456058f4a87426261ce53fbecb2d919d6a2d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846354"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Office 中 COM、VSTO 及 VBA 增益集的開發最佳作法
  如果您要開發適用于 Office 的 COM、VSTO 或 VBA 增益集，請遵循本文中所述的開發最佳作法。   這將有助於確保：

- 跨不同版本和 Office 部署的增益集的相容性。
- 為您的使用者和 IT 系統管理員降低增益集部署的複雜性。
- 增益集不會發生非預期的安裝或執行階段錯誤。

>注意：不支援使用[桌面橋接器](/windows/uwp/porting/desktop-to-uwp-root)來準備適用于 Windows STORE 的 COM、VSTO 或 VBA 增益集。 COM、VSTO 及 VBA 增益集無法散發于 Windows Store 或 Office Store。

## <a name="do-not-check-for-office-during-installation"></a>在安裝期間不檢查 Office
 建議您不要讓增益集偵測到在增益集安裝過程中是否已安裝 Office。 如果未安裝 Office，您可以安裝增益集，而且使用者將能夠在安裝 Office 之後存取它。

## <a name="use-embedded-interop-types-nopia"></a>使用內嵌的 Interop 類型（NoPIA）
如果您的方案使用 .NET 4.0 或更新版本，請使用內嵌的 interop 類型（NoPIA），而不是根據 Office 主要 Interop 元件（PIA）可轉散發套件。 使用類型內嵌可減少解決方案的安裝大小，並確保未來的相容性。 Office 2010 是隨附 PIA 可轉散發套件的最後一個 Office 版本。 如需詳細資訊，請參閱[逐步解說：從 Microsoft Office 元件內嵌類型資訊](https://msdn.microsoft.com/library/ee317478.aspx)和[類型等價和內嵌 interop 類型](/windows/uwp/porting/desktop-to-uwp-root)。

如果您的解決方案使用舊版的 .NET，建議您將方案更新為使用 .NET 4.0 或更新版本。 使用 .NET 4.0 或更新版本可減少較新版本 Windows 的執行時間必要條件。

## <a name="avoid-depending-on-specific-office-versions"></a>避免視特定 Office 版本而定
如果您的解決方案使用的功能僅適用于較新版本的 Office，請在執行時間確認功能是否存在（如果可能的話）（例如，使用例外狀況處理或藉由檢查版本）。 使用物件模型中支援的 Api，例如[Application. Version 屬性](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>)，驗證最小版本，而不是特定版本。 我們不建議您依賴 Office 二進位中繼資料、安裝路徑或登錄機碼，因為這些可能會在安裝、環境和版本之間變更。

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>同時啟用32位和64位的 Office 使用方式
除非您的解決方案相依于僅適用于特定位的程式庫，否則您的預設組建目標應該同時支援32位（x86）和64位（x64）。 64位版本的 Office 會隨著採用而增加，尤其是在大型資料環境中。 同時支援32位和64位，可讓您的使用者更輕鬆地在32位和64位版本的 Office 之間轉換。

撰寫 VBA 程式碼時，請使用64位安全的 declare 語句，並適當地轉換變數。 此外，請確定可以在執行32位或64位版本 Office 的使用者之間共用檔，方法是為每個位提供程式碼。 如需詳細資訊，請參閱[適用于應用程式的64位 Visual Basic 總覽](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview)。

## <a name="support-restricted-environments"></a>支援受限制的環境
您的解決方案不應要求使用者帳戶許可權提升或系統管理員許可權。 此外，此解決方案不應該相依于設定或改變：

- 目前的工作目錄。
- DLL 載入目錄。
- PATH 變數。

## <a name="change-the-save-location-of-shared-data-and-settings"></a>變更共用資料和設定的儲存位置
如果方案是由增益集和 Office 外部的進程所組成，請勿使用使用者的 [應用程式資料] 資料夾或登錄來交換增益集與外部進程之間的資料或設定。 相反地，請考慮使用使用者的暫存資料夾、documents 資料夾或您方案的安裝目錄。

## <a name="increment-the-version-number-with-each-update"></a>每次更新時遞增版本號碼
在您的方案中設定二進位檔的版本號碼，並隨著每次更新而遞增。 這可讓使用者更輕鬆地識別版本之間的變更，以及評估相容性。

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>提供最新 Office 版本的支援聲明
客戶會要求 Isv 針對在 Office 中執行的 COM、VSTO 及 VBA 增益集提供支援聲明。 列出您的明確支援聲明可協助使用 Office 365 ProPlus 準備就緒工具的客戶瞭解您的支援。

若要提供 Office 用戶端應用程式（例如 Word 或 Excel）的支援聲明，請先確認您的增益集是在目前的 Office 版本中執行，然後在您的增益集于未來的版本中時，認可以提供更新。 當 Microsoft 發行新組建或 Office 更新時，您不需要測試增益集。 Microsoft 很少會變更 Office 中的 COM、VSTO 和 VBA 擴充性平臺，而且這些變更將會妥善記載。

>重要事項： Microsoft 會針對就緒性報告和 ISV 連絡人資訊，維護一份支援的增益集清單。 若要列出您的增益集，請參閱[https://docs.microsoft.com/configmgr/desktop-analytics/ready-for-windows](https://docs.microsoft.com/configmgr/desktop-analytics/ready-for-windows)。

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>使用進程監視器來協助偵測安裝或載入問題
如果您的增益集在安裝或載入期間發生相容性問題，它們可能與檔案或登錄存取的問題有關。 使用[進程監視器](/sysinternals/downloads/procmon)或類似的偵錯工具，針對工作環境記錄和比較行為，以協助識別問題。
