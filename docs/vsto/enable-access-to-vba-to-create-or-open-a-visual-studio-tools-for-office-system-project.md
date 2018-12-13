---
title: 啟用存取權建立或開啟 Visual Studio Tools for Microsoft Office system 專案的 VBA
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f17c4e1481e7f33034e16d1e60a285b25c6f8230
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448987"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>啟用存取權建立或開啟 Visual Studio Tools for Microsoft Office system 專案的 VBA

您可以建立或開啟 Visual Studio Tools for Microsoft Office system 專案之前，您必須明確啟用對 Visual Basic for Applications (VBA) 在 Microsoft Office 中的專案系統的存取。

 Microsoft Office 開發專案需要存取 Visual Basic for Applications (VBA) 專案系統中 Microsoft Office Word 和 Microsoft Office Excel 時，即使專案不使用 Visual Basic 應用程式。 設計階段所支援 Visual Basic 和 C# 專案的控制項，取決於 Visual Basic for Applications 專案系統。

 某些 Microsoft Office 巨集病毒會嘗試自動執行 Visual Basic for Applications 專案系統，以傳播自己本身。 當您啟用對 Visual Basic for Applications 專案系統的存取時，您將會移除協助防止巨集病毒散播的保護機制。 不過仍會保留一般的巨集安全性，因此會使用您為 Office 應用程式所維護的巨集安全性層級和受信任發行者清單來判斷是否可以在電腦上執行巨集。

> [!NOTE]
> 這僅適用於開發電腦。 使用者電腦不需要啟用此選項即可執行 Office 方案。

 請務必注意，只是停用對 Visual Basic for Applications 專案系統的存取並不會保護您不受病毒的攻擊，這樣做只會在您的電腦真的遭到巨集病毒的危害時，停止將某些病毒散播到其他文件。 此選項預設為停用狀態，以便為電腦增加一個保護層，但是如果您依照下列安全性最佳做法進行再啟用此選項，您的電腦就比較不容易遭到病毒的危害。

 針對 Office 巨集病毒會在 「 高 」 或 「 非常高安全性層級，只信任來自巨集上執行 Office 證且已知的來源，並保持最新狀態的安全性修補程式和病毒掃描程式最佳保護。

 如需保護電腦不受病毒及其他惡意程式碼的詳細資訊，請參閱[ http://www.microsoft.com/protect ](http://www.microsoft.com/protect)。

 您可以啟用或停用此選項**信任存取 Visual Basic 專案**手動。

 如果出現 VBA 或 COM 錯誤，您可以修復 Office 的安裝。

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>若要啟用或停用存取 Visual Basic 專案

1. 按一下 [檔案]  索引標籤。

2. 按一下 [選項] 。

3. 按一下**信任中心**，然後按一下 **信任中心設定**。

4. 在**信任中心**，按一下 **巨集設定**。

5. 選取或取消選取**信任 VBA 專案物件模型存取**啟用或停用存取 Visual Basic 專案。

6. 按一下 [確定 **Deploying Office Solutions**]。

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>若要啟用或停用與 2007 Microsoft Office system 的 Visual Basic 專案的存取

1. 在**工具**功能表在 Word 或 Excel，指向**巨集**，然後按一下 **安全性**。

2. 在**安全性**對話方塊中，按一下 [**受信任的發行者**] 索引標籤。

3. 若要啟用，或清除此選項即可停用，請選取**信任存取 Visual Basic 專案**。

4. 按一下 [確定 **Deploying Office Solutions**]。

## <a name="to-set-your-office-macro-security-level"></a>設定 Office 巨集安全性層級

1. 按一下 [檔案]  索引標籤。

2. 按一下 [選項] 。

3. 按一下**信任中心**，然後按一下 **信任中心設定**。

4. 在**信任中心**，按一下 **巨集設定**。

5. 在**巨集設定**區段中，選取所需的設定。

6. 按一下 [確定 **Deploying Office Solutions**]。

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>若要設定 Office 巨集安全性層級與 2007 Microsoft Office system

1. 在**工具**功能表在 Word 或 Excel，指向**巨集**，然後按一下 **安全性**。

2. 在**安全性層級**索引標籤上，選取所需的設定。

    **安全性層級**包含每個層級的詳細資料 索引標籤。 如需詳細資訊，請參閱 Office 說明中的＜巨集安全性層級＞。

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>安裝 2007 Microsoft Office 系統的 VBA

1. 在控制台中執行**新增或移除程式**或**程式和功能**。

2. 中選取 Office**目前安裝的程式**清單。

3. 按一下 [ **變更**]。

4. 選取**新增或移除功能**，然後按一下 **繼續**。

5. 選取**選擇進階應用程式的自訂**，然後按一下 **下一步**。

6. 展開**Office 共用功能**中**選擇應用程式和工具的更新選項**清單。

7. 接下來，開啟下拉式選單**應用程式的 Visual Basic**，然後按一下**從我的電腦執行**。

8. 按一下 [ **繼續**]。

9. 按一下 [ **關閉**]。

## <a name="to-repair-your-installation-of-office"></a>修復 Office 的安裝

1. 在控制台中執行**新增或移除程式**或**程式和功能**。

2. 選取您在辦公室的版本**目前安裝的程式**清單。

3. 按一下 [ **變更**]。

4. 選取**重新安裝或修復**，然後按一下 **下一步**。

5. 選取**偵測並修復 Office 中的安裝錯誤**，然後按一下 **安裝**。

## <a name="see-also"></a>另請參閱

 [保護 Office 方案](../vsto/securing-office-solutions.md)