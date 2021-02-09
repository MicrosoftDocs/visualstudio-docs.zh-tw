---
title: 開發最佳作法： Office 中的 COM、VSTO、& VBA 增益集
description: 瞭解開發 Microsoft Office 的 COM、VSTO 及 VBA 增益集時的建議最佳作法。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d5470c138d4339356ca9f8c79cb5ab274dd99019
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897560"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Office 中 COM、VSTO 及 VBA 增益集的開發最佳作法
  如果您正在開發適用于 Office 的 COM、VSTO 或 VBA 增益集，請遵循本文中所述的開發最佳做法。   這將有助於確保：

- 跨不同版本與 Office 部署的增益集相容性。
- 降低使用者和 IT 系統管理員增益集部署的複雜度。
- 增益集的非預期安裝或執行時間失敗不會發生。

>注意：不支援使用 [傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root) 來準備您的 COM、VSTO 或適用于 Windows STORE 的 VBA 增益集。 COM、VSTO 及 VBA 增益集無法在 Windows Store 或 Office Store 中散發。

## <a name="do-not-check-for-office-during-installation"></a>在安裝期間不檢查 Office
 我們不建議您讓增益集偵測到增益集安裝程式期間是否已安裝 Office。 如果未安裝 Office，您可以安裝增益集，使用者將能夠在安裝 Office 之後存取該增益集。

## <a name="use-embedded-interop-types-nopia"></a>使用內嵌的 Interop 類型 (NoPIA) 
如果您的方案使用 .NET 4.0 或更新版本，請使用內嵌的 interop 類型 (NoPIA) 而不是根據 Office 主要 Interop 元件 (PIA) 可轉散發套件。 使用型別內嵌可減少解決方案的安裝大小，並確保未來的相容性。 Office 2010 是發行 PIA 可轉散發套件的最後一個版本。 如需詳細資訊，請參閱 [逐步解說：從 Microsoft Office 元件內嵌型別資訊](/previous-versions/ee317478(v=vs.140)) 和 [類型等價和內嵌 interop 類型](/windows/uwp/porting/desktop-to-uwp-root)。

如果您的方案使用舊版的 .NET，建議您將方案更新為使用 .NET 4.0 或更新版本。 使用 .NET 4.0 或更新版本可減少較新版 Windows 的執行時間必要條件。

## <a name="avoid-depending-on-specific-office-versions"></a>避免因特定 Office 版本而異
如果您的方案使用的功能只適用于較新版本的 Office，請在運行 (時間) 功能層級，確認功能 (存在，例如，使用例外狀況處理或檢查版本) 。 使用物件模型中支援的 Api （例如， [應用程式版本屬性](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>)），驗證最低版本（而不是特定版本）。 我們不建議您依賴 Office 二進位中繼資料、安裝路徑或登錄機碼，因為這些可能會在安裝、環境和版本之間變更。

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>啟用32位和64位辦公室的使用方式
除非您的方案相依于僅適用于特定位數的程式庫，否則您的預設組建目標應該支援32位 (x86) 和64位 (x64) 。 64位版本的 Office 在採用時逐漸增加，尤其是在大型資料環境中。 同時支援32位和64位，可讓使用者更輕鬆地在32位和64位版本的 Office 之間轉換。

撰寫 VBA 程式碼時，請使用64位安全的 declare 語句，並適當地轉換變數。 此外，您可以提供每個位的程式碼，以確保可在執行32位或64位版本 Office 的使用者之間共用檔。 如需詳細資訊，請參閱 [應用程式的64位 Visual Basic 總覽](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview)。

## <a name="support-restricted-environments"></a>支援受限的環境
您的解決方案不應要求使用者帳戶提升許可權或系統管理員許可權。 此外，此解決方案不應依賴設定或改變：

- 目前的工作目錄。
- DLL 載入目錄。
- 路徑變數。

## <a name="change-the-save-location-of-shared-data-and-settings"></a>變更共用資料和設定的儲存位置
如果解決方案包含增益集和 Office 外部的進程，請勿使用使用者的應用程式資料檔案夾或登錄來交換增益集與外部進程之間的資料或設定。 相反地，請考慮使用使用者的 [暫存資料夾]、[檔] 資料夾，或您解決方案的安裝目錄。

## <a name="increment-the-version-number-with-each-update"></a>每次更新時遞增版本號碼
在您的方案中設定二進位檔的版本號碼，並使用每個更新來遞增。 這可讓使用者更輕鬆地識別版本之間的變更，並評估相容性。

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>為最新版本的 Office 提供支援聲明
客戶要求 Isv 針對在 Office 中執行的 COM、VSTO 及 VBA 增益集提供支援聲明。 列出您的明確支援聲明，可協助客戶使用 Microsoft 365 應用程式，以取得企業就緒性工具以瞭解您的支援。

若要提供 Office 用戶端應用程式的支援語句 (例如 Word 或 Excel) ，請先確認您的增益集是否在目前的 Office 版本中執行，然後在您的增益集于未來版本中中斷時，認可以提供更新。 當 Microsoft 發行新的組建或 Office 更新時，您不需要測試您的增益集。 Microsoft 很少會變更 Office 中的 COM、VSTO 和 VBA 擴充性平臺，而且這些變更將妥善記載。

>重要事項： Microsoft 會維護支援的增益集清單，以及 ISV 連絡人資訊。 若要取得您的增益集清單，請參閱 [/configmgr/desktop-analytics/ready-for-windows](/configmgr/desktop-analytics/ready-for-windows)。

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>使用進程監視器協助偵測安裝或載入問題
如果增益集在安裝或載入期間發生相容性問題，這些問題可能與檔案或登錄存取的問題有關。 使用 [進程監視器](/sysinternals/downloads/procmon) 或類似的偵錯工具，針對工作環境記錄和比較行為，以協助找出問題。