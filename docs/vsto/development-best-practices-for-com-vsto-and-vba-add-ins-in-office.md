---
title: COM、 VSTO 和 VBA 增益集 Office 的開發最佳作法
ms.custom: ''
ms.date: 07/25/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3f821b9769b9353fbee6379ddc1b3826f87ac2de
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671089"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>COM、 VSTO 和 VBA 增益集 Office 的開發最佳作法
  如果您正在適用於 Office 開發 COM、 VSTO 或 VBA 增益集，請遵循本文中所述的開發最佳作法。   這有助於確保：

-  您的增益集跨不同版本和部署的 Office 相容性。
-  降低您的使用者和 IT 系統管理員的增益集部署的複雜度。
-  不會發生非預期的安裝或執行階段失敗的增益集。

>注意： 使用[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)來準備您的 COM、 VSTO 或 VBA 增益集不支援 Windows 市集。 無法在 Windows 市集 」 或 「 Office 市集散發 COM、 VSTO 和 VBA 增益集。 
  
## <a name="do-not-check-for-office-during-installation"></a>不要在安裝期間檢查 Office  
 我們不建議具有偵測增益集安裝程序期間是否已安裝 Office 增益集。 如果未安裝 Office，您可以安裝增益集，以及使用者將能夠存取它，在安裝 Office 之後。 
  
## <a name="use-embedded-interop-types-nopia"></a>使用內嵌的 Interop 類型 (NoPIA)  
如果您的方案會使用.NET 4.0 或更新版本中，使用內嵌的 interop 類型 (NoPIA) 而不是取決於 Office 主要 Interop 組件 (PIA) 可轉散發套件。 使用內嵌型別可縮小安裝您的方案，並確保未來的相容性。 Office 2010 為 Office PIA 可轉散發套件隨附的最後一個版本。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 從 Microsoft Office 組件內嵌類型資訊](https://msdn.microsoft.com/library/ee317478.aspx)並[類型等價和內嵌 interop 類型](/windows/uwp/porting/desktop-to-uwp-root)。

如果您的方案會使用較早版本的.NET，我們建議您更新您的解決方案，以使用.NET 4.0 或更新版本。 使用.NET 4.0 或更新版本，可減少在較新版本的 Windows 上的執行階段必要條件。
  
## <a name="avoid-depending-on-specific-office-versions"></a>避免特定的 Office 版本而定。  
如果您的解決方案會使用僅供以較新版本的 Office 的功能，請確認在執行階段 （例如，使用例外狀況處理，或藉由檢查版本） 的功能存在 （可能的話，請在功能層級）。 驗證最小版本，而不是特定的版本，在物件模型中，使用支援的 Api，例如[Application.Version 屬性](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>)。 我們不建議您需要 Office 二進位中繼資料、 安裝路徑，或登錄機碼，因為這些可以在安裝、 環境和版本之間變更。

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>啟用 32 位元和 64 位元 Office 使用   
預設的 build 目標應支援 (x86) 32 位元和 64 位元 (x64)，除非您的解決方案視只適用於特定的位元的程式庫。 64 位元版本的 Office 增加的採用，尤其是在巨量資料環境。 支援 32 位元和 64 位元更容易為您的使用者，32 位元和 64 位元版本 Office 之間的轉換。

在撰寫 VBA 程式碼，使用 64 位元安全 declare 陳述式，並轉換為適當的變數。 此外，請確定，可以藉由提供每一個位元程式碼執行 Office 32 位元或 64 位元版本的使用者之間共用文件。 如需詳細資訊，請參閱 <<c0> [ 應用程式概觀的 64 位元 Visual Basic](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview)。

## <a name="support-restricted-environments"></a>支援限制的環境   
您的解決方案應該不需要使用者帳戶提高權限或系統管理員權限。 此外，解決方案不應該相依於設定或變更：

- 目前的工作目錄。
- DLL 載入目錄。
- 路徑變數中。

## <a name="change-the-save-location-of-shared-data-and-settings"></a>變更儲存共用的資料和設定的位置
如果方案是由增益集和外部 Office 處理序所組成，請勿使用使用者的應用程式資料資料夾或登錄來交換資料或增益集和外部處理序之間的設定。 相反地，請考慮使用使用者的暫存資料夾、 文件 資料夾中或您方案的安裝目錄。

## <a name="increment-the-version-number-with-each-update"></a>遞增版本號碼，每次更新
設定方案中的二進位檔的版本號碼，並增加每次更新。 這會讓使用者更輕鬆地找出版本之間變更，並評估相容性。

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>提供 Office 的最新版本的支援聲明
客戶都詢問 Isv 能夠提供其 COM、 VSTO 和 VBA 增益集，在 Office 中執行的支援聲明。 列出您使用 Office 365 ProPlus 的明確支援陳述式可協助客戶準備就緒工具了解您的支援人員。 

若要提供 Office 用戶端應用程式 （例如 Word 或 Excel） 的支援聲明，先確認您的增益集執行在目前的 Office 版本中，然後認可來提供更新，如果您的增益集中斷在未來的版本。 您沒有 Microsoft 發行新的組建或 Office 的更新時，測試您的增益集。 Microsoft 很少變更在 Office 中的 COM、 VSTO 和 VBA 擴充性平台，這些變更將會有完善的記載。

>重要事項： Microsoft 會維護一份支援增益集的就緒程度報告和 ISV 的連絡資訊。 若要取得增益集內所列，請參閱[ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows)。

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>使用處理序監視器，以協助偵錯安裝或載入問題
如果增益集有在安裝或負載期間的相容性問題，他們可能會與檔案或登錄存取問題。 使用[處理序監視](/sysinternals/downloads/procmon)或類似的偵錯工具，來記錄和比較行為的工作環境，以協助找出問題。
