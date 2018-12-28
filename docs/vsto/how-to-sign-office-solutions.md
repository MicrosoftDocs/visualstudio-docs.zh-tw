---
title: HOW TO：簽署 Office 方案
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 076cfcb6b63d650665e79a1e2d522595d4a82922
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804691"
---
# <a name="how-to-sign-office-solutions"></a>HOW TO：簽署 Office 方案
  如果您登入解決方案，您可以授與信任給方案做為辨識項使用的憑證。 您可以使用相同的憑證用於多個方案，並沒有額外的安全性原則更新，所有的解決方案將會信任。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 如果您以手動方式編輯應用程式和部署資訊清單使用資訊清單產生和編輯工具 (*mage.exe*並*mageui.exe*)，您可以使用它們之前，您必須重新簽署資訊清單。 如需詳細資訊，請參閱[＜How to：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。

## <a name="sign-by-using-a-certificate"></a>使用憑證來簽署
 憑證是包含唯一的索引鍵和方案發行者的身分識別的檔案。 您可以向憑證授權單位購買憑證或建立您自己的憑證並加以簽署的憑證授權單位。

 Visual Studio 會使用暫時憑證，來啟用偵錯 Office 方案。 您不應該在已部署的方案中使用的暫時憑證，做為辨識項。

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>若要使用憑證來簽署 Office 方案

1.  在 **專案**功能表上，按一下_SolutionName_**屬性**。

2.  按一下 [簽署]索引標籤。

3.  選取 **簽署 ClickOnce 資訊清單**。

4.  找出憑證，依序按一下**從存放區中選取**或是**從檔案選取**並瀏覽至憑證。

5.  若要確認正在使用正確的憑證，請按一下**更多詳細資料**檢視憑證資訊。

## <a name="see-also"></a>另請參閱

- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [授與信任給 Office 方案](../vsto/granting-trust-to-office-solutions.md)
- [專案設計工具、簽署頁面](../ide/reference/signing-page-project-designer.md)
