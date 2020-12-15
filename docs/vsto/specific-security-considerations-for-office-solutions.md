---
title: Office 方案的特定安全性考慮
description: 瞭解 Microsoft .NET Framework 和 Microsoft Office 所提供的安全性功能如何協助保護您的 Office 解決方案免于安全性威脅。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0da77067931d35ee63a9ccc9b0de85752157772b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524299"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Office 方案的特定安全性考慮
  Microsoft .NET Framework 和 Microsoft Office 所提供的安全性功能，可協助保護您的 Office 解決方案免於可能的安全性威脅。 本主題說明一些這類威脅，並提供建議協助您免於威脅。 本主題也包含 Microsoft Office 安全性設定如何影響 Office 方案的相關資訊。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>受信任的程式碼在新的惡意檔中重新建立用途
 攻擊者可能取得專用於特定用途的受信任程式碼，例如下載求職申請的個人資訊，然後在其他文件中重複使用，例如工作表。 該程式碼並不知道原始文件未執行，因而可能讓其他威脅有機可趁；例如，當不同使用者開啟文件時，以提高的權限洩露個人資訊或執行程式碼。 或者，攻擊者可以修改工作表中的資料，以便在傳送給犧牲者時，其行為意外。 藉由變更連結至程式碼之工作表的值、公式或呈現特性，惡意使用者很可能傳送已修改的檔案，進而攻擊另一位使用者。 使用者也可能修改工作表中的值，存取他們不應該查看的資訊。

 由於組件位置和文件位置必須有足夠的辨識項來執行，所以並不容易裝載這類攻擊。 例如在電子郵件附件或未受信任之內部網路伺服器上的文件，就沒有足夠權限來執行。

 這類程式碼為了進行攻擊，本身的撰寫方式必須可使其基於不受信任的資料進行決策。 範例會建立具有隱藏儲存格的工作表，其中包含資料庫伺服器名稱。 使用者提交工作表至 ASPX 網頁，這會使用 SQL 驗證和硬式編碼的 SA 密碼，嘗試連線到該伺服器。 攻擊者可能使用不同的電腦名稱來取代隱藏資料格的內容，並取得 SA 密碼。 若要避免這個問題，請勿將密碼硬式編碼，並且一律檢查伺服器 ID 是否列於已知安全的伺服器內部清單，之後才能存取該伺服器。

### <a name="recommendations"></a>建議

- 一律驗證輸入和資料，不論其來自使用者、文件、資料庫、Web 服務或任何其他來源。

- 若要公開特定類型的功能須格外謹慎，例如代表使用者取得有權限的資料，並將該資料放入受保護的活頁簿。

- 根據應用程式類型而定，在執行任何程式碼之前，先確認原始文件正在執行是合理的做法。 例如，請確認該程式碼於儲存在已知且安全位置上的文件中執行。

- 如果您的應用程式會執行任何特殊權限的動作，則在文件開啟時顯示警告也可能是不錯的主意。 例如，您可能會建立啟動顯示畫面或啟動對話方塊，指出此應用程式會存取個人資訊，然後讓使用者選擇繼續或取消。 如果使用者從看似無害的文件接收這類警告，該使用者將能在任何項目遭到入侵之前，先結束應用程式。

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Outlook 物件模型防護封鎖的程式碼
 Microsoft Office 可以限制程式碼使用物件模型中的特定屬性、方法和物件。 藉由限制這些物件的存取權，Outlook 有助於防止電子郵件蠕蟲和病毒使用物件模型來因應惡意用途。 這項安全性功能稱為 Outlook 物件模型保護。 如果 VSTO 增益集在啟用物件模型保護時嘗試使用受限制的屬性或方法，Outlook 會顯示安全性警告，讓使用者停止作業，或讓使用者在一段有限的時間內授與屬性或方法的存取權。 如果使用者停止作業，使用 Visual Studio 中 Office 方案建立的 Outlook VSTO 增益集將會擲回 <xref:System.Runtime.InteropServices.COMException>。

 物件模型保護對 VSTO 增益集的作用有幾種方式，取決於 Outlook 是否與 Microsoft Exchange Server 搭配使用：

- 如果 Outlook 未搭配使用 Exchange，系統管理員便可以啟用或停用在該電腦上所有 VSTO 增益集的物件模型保護。

- 如果 Outlook 搭配使用 Exchange，系統管理員便可以啟用或停用在該電腦上所有 VSTO 增益集的物件模型保護，或者系統管理員可以指定特定 VSTO 增益集可以在不遇到物件模型保護的情況下執行。 系統管理員也可以針對物件模型的某些區域，修改物件模型保護行為。 例如，系統管理員可以自動允許 VSTO 增益集以程式設計的方式傳送電子郵件，即使物件模型保護已啟用也一樣。

  從 Outlook 2007 開始，物件模型保護的行為已變更為改善開發人員和使用者體驗，同時協助保護 Outlook 安全。 如需詳細資訊，請參閱 [Outlook 2007 中的程式碼安全性變更](/previous-versions/office/developer/office-2007/bb226709(v=office.12))。

### <a name="minimize-object-model-guard-warnings"></a>將物件模型防護警告降至最低
 當您使用受限制的屬性和方法時，為了避免安全性警告，請確定您的 VSTO 增益集從專案中 `Application` 類別的 `ThisAddIn` 欄位取得 Outlook 物件。 如需此欄位的詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

 只有從這個物件取得之 Outlook 物件，可受到物件模型保護信任。 相反地，從新的 `Microsoft.Office.Interop.Outlook.Application` 物件取得之物件不受信任，而且如果物件模型保護已啟用，則受限制的屬性和方法將會引發安全性警告。

 如果物件模型保護已啟用，則下列程式碼範例會顯示安全性警告。 `Microsoft.Office.Interop.Outlook.MailItem` 類別的 `To` 屬性受物件模型保護限制。 `Microsoft.Office.Interop.Outlook.MailItem`物件不受信任 `Microsoft.Office.Interop.Outlook.Application` ，因為程式碼會從使用 **new** 運算子所建立的來取得它，而不是從欄位取得它 `Application` 。

 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]

 下列程式碼範例將示範如何使用物件模型保護所信任之物件的 [限制為] 屬性 `Microsoft.Office.Interop.Outlook.MailItem` 。 此程式碼會使用受信任的 `Application` 欄位以取得 `Microsoft.Office.Interop.Outlook.MailItem`。

 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]

> [!NOTE]
> 如果 Outlook 與 Exchange 搭配使用，則從 `ThisAddIn.Application` 取得所有 Outlook 物件並不保證 VSTO 增益集可存取整個 Outlook 物件模型。 例如，如果 Exchange 系統管理員設定 Outlook 自動拒絕使用 Outlook 物件模型存取位址資訊的所有嘗試，則 Outlook 將不會允許先前的程式碼範例存取 To 屬性，即使該程式碼範例使用了受信任的欄位也一樣 `ThisAddIn.Application` 。

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>指定使用 Exchange 時要信任的增益集
 當 Outlook 與 Exchange 搭配使用時，系統管理員便可以指定特定 VSTO 增益集可以在不遇到物件模型保護的情況下執行。 使用 Visual Studio 中 Office 方案建立的 Outlook VSTO 增益集無法個別受到信任，它們只能以群組方式受到信任。

 Outlook 會根據 VSTO 增益集進入點 DLL 的雜湊碼來信任 VSTO 增益集。 所有目標的 Outlook VSTO 增益集都 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 使用相同的進入點 DLL (*VSTOLoader.dll*) 。 這表示，如果系統管理員信任任何目標為的 VSTO 增益集， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 而不會遇到物件模型保護，則所有其他以的 Vsto 增益集 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 也會受到信任。 如需信任特定 VSTO 增益集，藉此在不遇到物件模型保護之情況下執行的詳細資訊，請參閱 [指定 Outlook 用來管理病毒防護功能的方法](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12))。

## <a name="permission-changes-do-not-take-effect-immediately"></a>許可權變更不會立即生效
 如果系統管理員調整文件或組件的權限，則使用者必須結束，然後再重新啟動所有 Office 應用程式，藉此強制執行這些變更。

 裝載 Microsoft Office 應用程式的其他應用程式，也可以防止新的權限付諸執行。 當變更安全性原則時，使用者應結束所有已裝載 Office 或獨立使用 Office 的應用程式。

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Microsoft Office 系統中的 [信任中心] 設定不會影響增益集或檔層級自訂
 使用者可以防止 VSTO 增益集載入，方法是設定 [信任中心] 的選項。 不過，這些信任設定不會影響使用 Visual Studio 中 Office 方案建立的 VSTO 增益集和文件層級自訂。

 如果使用者使用 [信任中心] 防止載入 VSTO 增益集，將不會載入下列類型的 VSTO 增益集：

- Managed 和 Unmanaged COM VSTO 增益集。

- Managed 和 Unmanaged 智慧文件。

- Managed 和 Unmanaged 自動化 VSTO 增益集。

- Managed 和 Unmanaged 即時資料元件。

  下列程序描述使用者如何使用 [信任中心]  來限制 VSTO 增益集無法載入 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 和 Microsoft Office 2010。 這些程序不會影響 Visual Studio 中使用 Office 開發工具所建立的 VSTO 增益集或自訂。

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-office_15_short-applications"></a>在 Microsoft Office 2010 和 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 應用程式停用 VSTO 增益集

1. 選擇 [檔案]  索引標籤。

2. 選擇 [應用程式名稱選項]   按鈕。

3. 在分類窗格中，選擇 [信任中心] 。

4. 在詳細資料窗格中，選擇 [信任中心設定] 。

5. 在分類窗格中，選擇 [增益集] 。

6. 在 [詳細資料] 窗格中，選取 [要求應用程式增益集由受信任的發行者簽署]  或 [停用所有應用程式增益集] 。

## <a name="see-also"></a>另請參閱
- [保護 Office 方案](../vsto/securing-office-solutions.md)
