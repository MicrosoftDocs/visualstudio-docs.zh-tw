---
title: 建立/開啟 VSTO 系統專案的 VBA 存取權
titleSuffix: ''
description: 瞭解您必須明確啟用 Office VBA 專案系統的存取權，才能建立或開啟 Visual Studio Tools for Office 系統專案。
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62477f7cd37a7d5a416e8f42fb7eb2d2a8e43828
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846125"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>啟用 VBA 存取以建立或開啟 Microsoft Office 系統專案的 Visual Studio Tools

您必須明確啟用 Microsoft Office 中 Visual Basic for Applications (VBA) 專案系統的存取權，才能建立或開啟 Visual Studio Tools 系統專案的 Microsoft Office。

 Microsoft Office 的開發專案需要在 Microsoft Office Word 和 Microsoft Office Excel 中存取 Visual Basic for Applications (VBA) 專案系統，即使專案不使用 Visual Basic for Applications 也一樣。 執行階段所支援 Visual Basic 和 C# 專案的控制項，取決於 Visual Basic for Applications 專案系統。

 某些 Microsoft Office 巨集病毒會嘗試自動執行 Visual Basic for Applications 專案系統，以傳播自己本身。 當您啟用對 Visual Basic for Applications 專案系統的存取時，您將會移除協助防止巨集病毒散播的保護機制。 不過仍會保留一般的巨集安全性，因此會使用您為 Office 應用程式所維護的巨集安全性層級和受信任發行者清單來判斷是否可以在電腦上執行巨集。

> [!NOTE]
> 這僅適用於開發電腦。 終端使用者電腦不需要啟用此選項即可執行 Office 方案。

 請務必注意，只是停用對 Visual Basic for Applications 專案系統的存取並不會保護您不受病毒的攻擊，這樣做只會在您的電腦真的遭到巨集病毒的危害時，停止將某些病毒散播到其他文件。 此選項預設為停用狀態，以便為電腦增加一個保護層，但是如果您依照下列安全性最佳做法進行再啟用此選項，您的電腦就比較不容易遭到病毒的危害。

 針對 Office 巨集病毒的最佳保護是在高或非常高的安全性層級上執行 Office、只信任經過驗證、已知來源的宏，以及隨時掌握最新的安全性修補程式和病毒掃描程式。

 您可以手動啟用或停用 **Visual Basic 專案的 [信任存取** ] 選項。

 如果出現 VBA 或 COM 錯誤，您可以修復 Office 的安裝。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>若要啟用或停用 Visual Basic 專案的存取權

1. 按一下 [檔案]  索引標籤。

2. 按一下 [選項]。

3. 按一下 [ **信任中心**]，然後按一下 [ **信任中心設定**]。

4. 在 [ **信任中心**] 中，按一下 [ **宏設定**]。

5. 核取或取消核取 **VBA 專案物件模型的 [信任存取權** ]，以啟用或停用 Visual Basic 專案的存取權。

6. 按一下 [確定]。

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>若要啟用或停用具有 2007 Microsoft Office 系統之 Visual Basic 專案的存取權

1. 在 Word 或 Excel 的 [ **工具** ] 功能表上，指向 [ **宏**]，然後按一下 [ **安全性**]。

2. 在 [ **安全性** ] 對話方塊中，按一下 [ **信任的發行者** ] 索引標籤。

3. 選取以啟用或清除 [停用]， **Visual Basic 專案的 [信任存取**]。

4. 按一下 [確定]。

## <a name="to-set-your-office-macro-security-level"></a>設定 Office 巨集安全性層級

1. 按一下 [檔案]  索引標籤。

2. 按一下 [選項]。

3. 按一下 [ **信任中心**]，然後按一下 [ **信任中心設定**]。

4. 在 [ **信任中心**] 中，按一下 [ **宏設定**]。

5. 在 [ **宏設定** ] 區段中，選取所需的設定。

6. 按一下 [確定]。

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>使用 2007 Microsoft Office 系統設定 Office 宏安全性等級

1. 在 Word 或 Excel 的 [ **工具** ] 功能表上，指向 [ **宏**]，然後按一下 [ **安全性**]。

2. 在 [ **安全性等級** ] 索引標籤上，選取所需的設定。

    [ **安全性層級** ] 索引標籤包含每個層級的詳細資料。 如需詳細資訊，請參閱 Office 說明中的＜巨集安全性層級＞。

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>安裝 2007 Microsoft Office 系統的 VBA

1. 在主控台中，執行 [ **新增或移除程式** ] 或 [ **程式和功能**]。

2. 在 [ **目前安裝的程式** ] 清單中選取 [Office]。

3. 按一下 [變更]。

4. 選取 [ **新增或移除功能**]，然後按一下 [ **繼續**]。

5. 選取 **[選擇應用程式的自訂**]，然後按 **[下一步]**。

6. 展開 [**選擇應用程式和工具的更新選項**] 清單中的 [ **Office 共用功能**]。

7. 開啟 **Visual Basic for Applications** 旁的下拉式功能表，然後按一下 [ **從我的電腦執行**]。

8. 按一下 **[繼續]** 。

9. 按一下 [關閉]  。

## <a name="to-repair-your-installation-of-office"></a>修復 Office 的安裝

1. 在主控台中，執行 [ **新增或移除程式** ] 或 [ **程式和功能**]。

2. 在 [ **目前安裝的程式** ] 清單中選取您的 Office 版本。

3. 按一下 [變更]。

4. 選取 [ **重新安裝或修復**]，然後按 **[下一步]**。

5. 選取 [ **在我的 Office 安裝中偵測及修復錯誤**]，然後按一下 [ **安裝**]。

## <a name="see-also"></a>另請參閱
- [保護 Office 方案](../vsto/securing-office-solutions.md)
