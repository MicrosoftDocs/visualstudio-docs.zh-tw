---
title: "開發最佳做法 COM、 VSTO 和 VBA 的增益集在辦公室 |Microsoft 文件"
ms.custom: 
ms.date: 07/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: 
helpviewer_keywords: 
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2158
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8985b3bb6e20b24b86174286104158c8830de971
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="development-best-practices-for-com-vsto-and-vba--add-ins-in-office"></a>開發的 COM、 VSTO 和 VBA 的增益 Office 中的最佳作法
  如果您正在開發 Office COM 的 VBA VSTO 增益集，請遵循本文中所述的開發最佳作法。   這將有助於確保：

-  您的增益集和部署 Office 的不同版本之間的相容性。
-  之複雜性已降低增益集部署您的使用者和 IT 系統管理員。
-  不會發生非預期的增益集安裝或執行階段失敗。

>請注意： 使用[桌面橋接器](/windows/uwp/porting/desktop-to-uwp-root)準備您的 COM VSTO 或 VBA 增益集不支援 Windows 市集。 無法在 Windows 市集或 Office 市集散發 COM、 VSTO 和 VBA 的增益。 
  
## <a name="do-not-check-for-office-during-installation"></a>不要在安裝期間檢查 Office  
 我們不建議讓偵測在增益集安裝程序是否已安裝 Office 增益集。 如果未將 Office 安裝，您可以安裝增益集，以及使用者可以存取它，在安裝 Office 之後。 
  
## <a name="use-embedded-interop-types-nopia"></a>使用內嵌 Interop 類型 (NoPIA)  
如果您的方案會使用.NET 4.0 或更新版本中，使用內嵌 interop 類型 (NoPIA) 而不是根據 Office 主要 Interop 組件 (PIA) 可轉散發套件。 使用內嵌型別可縮小安裝您的方案，並確保未來的相容性。 Office 2010 是 Office PIA 可轉散發套件隨附的最後一個版本。 如需詳細資訊，請參閱[逐步解說： 從 Microsoft Office 組件內嵌類型資訊](https://msdn.microsoft.com/en-us/library/ee317478.aspx)和[類型等價和內嵌 Interop 類型](/windows/uwp/porting/desktop-to-uwp-root)。

如果您的方案使用較早版本的.NET，我們建議您更新方案中，以便使用.NET 4.0 或更新版本。 使用.NET 4.0 或更新版本，可降低在較新版本的 Windows 執行階段必要條件。
  
## <a name="avoid-depending-on-specific-office-versions"></a>避免根據特定的 Office 版本  
如果您的方案使用僅供以較新版本的 Office 的功能，請確認在執行階段 （例如，使用例外狀況處理或正在檢查的版本） 的功能有 （可能的話，請在功能層級）。 驗證最小版本中，而不是特定版本，例如在物件模型中，使用支援的 Api [Application.Version 屬性](https://msdn.microsoft.com/en-us/library/office/microsoft.office.interop.excel._application.version.aspx)。 我們不建議您需要 Office 二進位中繼資料、 安裝路徑，或登錄機碼，因為這些可能會安裝、 環境和版本之間變更。

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>啟用 32 位元和 64 位元 Office 使用   
您預設建置 」 目標應該支援 (x86) 32 位元和 64 位元 (x64)，除非您的方案而定只適用於特定的位元版本的程式庫。 64 位元版本的 Office 增加採用，尤其是在巨量資料的環境中。 32 位元和 64 位元的支援方便使用者 Office 32 位元和 64 位元版本之間轉換。

在撰寫 VBA 程式碼時，使用 64 位元安全宣告陳述式，並轉換為適當的變數。 此外，請確定文件，可以在執行 32 位元或 64 位元版本的 Office 所提供的程式碼的每一個位元版本的使用者之間共用。 如需詳細資訊，請參閱[應用程式概觀的 64 位元 Visual Basic](https://msdn.microsoft.com/en-us/library/office/gg264421.aspx)。

## <a name="support-restricted-environments"></a>支援限制的環境   
您的方案應該不需要使用者帳戶的提高權限或系統管理員權限。 此外，方案不應依賴設定或變更：

- 目前的工作目錄。
- DLL 載入目錄。
- PATH 變數中。

## <a name="change-the-save-location-of-shared-data-and-settings"></a>在儲存位置的共用的資料和設定
如果方案包含增益集和辦公室外部的程序，請勿使用使用者的應用程式資料資料夾或登錄來交換資料或增益集和外部處理序之間的設定。 相反地，請考慮使用使用者的暫存資料夾、 文件 資料夾或您方案的安裝目錄。

## <a name="increment-the-version-number-with-each-update"></a>遞增與每個更新的版本號碼
設定您的方案中的二進位檔的版本號碼，並遞增與每個更新。 這會讓使用者更輕鬆地識別版本之間變更，並評估相容性。

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>提供 Office 的最新版本的支援聲明
客戶要求 Isv 提供其 COM、 VSTO 和 VBA 的增益，在 Office 中執行的支援聲明。 列出使用 Office 365 ProPlus 您明確支援的陳述式可協助客戶整備工具了解您的支援人員。 

若要提供 Office 用戶端應用程式 （例如，Word 或 Excel） 的支援聲明，先確認您的增益集執行在目前 Office 版本中，然後認可如果增益集線的未來版本中提供的更新。 您沒有 Microsoft 發行新版本或 Office 的更新時，測試您的增益集。 Microsoft 不常變更 office 中的 COM、 VSTO 和 VBA 擴充平台，這些變更將會完整記錄。

>重要事項： Microsoft 維護一份支援增益集的整備報表和 ISV 連絡資訊。 若要取得增益集所列，請參閱[https://aka.ms/readyforwindows](https://aka.ms/readyforwindows)。

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>使用處理序監視協助偵錯安裝或載入問題
如果增益集具有 相容性問題在安裝或載入期間，它們可能相關的檔案或登錄存取問題。 使用[處理序監視](/sysinternals/downloads/procmon)或類似的偵錯工具，來記錄和比較行為，找出問題的工作環境。
