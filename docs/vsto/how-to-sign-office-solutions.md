---
title: 如何：簽署 Office 方案
description: 瞭解如何使用憑證做為辨識項，將信任授與您的 Microsoft Office 解決方案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3135962c8476fdb6970fc137e689c638299f8f81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927635"
---
# <a name="how-to-sign-office-solutions"></a>如何：簽署 Office 方案
  如果您簽署解決方案，則可以使用憑證做為辨識項，將信任授與解決方案。 您可以將相同的憑證用於多個解決方案，而且所有解決方案都將受信任，而不需要額外的安全性原則更新。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 如果您使用資訊清單產生和編輯工具 (*mage.exe* 和 *mageui.exe*) ，手動編輯應用程式和部署資訊清單，您必須先重新簽署資訊清單，才能加以使用。 如需詳細資訊，請參閱[如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。

## <a name="sign-by-using-a-certificate"></a>使用憑證簽署
 憑證是一個檔案，其中包含唯一金鑰和方案發行者的身分識別。 您可以從憑證授權單位單位購買憑證，或建立自己的憑證並讓憑證授權單位單位簽署。

 Visual Studio 使用暫時性憑證來簽署 Office 方案，以啟用調試。 您不應該在已部署的解決方案中使用暫時性憑證做為辨識項。

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>使用憑證簽署 Office 方案

1. 在 [**專案**] 功能表上，按一下 [_解決方案名稱_]**屬性**。

2. 按一下 [ **簽署** ] 索引標籤。

3. 選取 **[簽署 ClickOnce 資訊清單**]。

4. 按一下 [ **從存放區選取** ] 或 [ **從檔案選取** ]，然後流覽至憑證，以找出憑證。

5. 若要確認正在使用正確的憑證，請按一下 [ **詳細資料** ] 以查看憑證資訊。

## <a name="see-also"></a>另請參閱

- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [授與信任給 Office 方案](../vsto/granting-trust-to-office-solutions.md)
- [專案設計工具、簽署頁](../ide/reference/signing-page-project-designer.md)
