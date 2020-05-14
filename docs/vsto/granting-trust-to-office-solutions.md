---
title: 授予 Office 解決方案的信任
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303299"
---
# <a name="grant-trust-to-office-solutions"></a>授予 Office 解決方案的信任
  向 Office 解決方案授予信任意味著修改每個目的電腦的安全性原則，以信任解決方案程式集、應用程式清單、部署清單和文檔。 您或最終使用者都可以信任 Office 解決方案。

 您可以通過簽署應用程式和部署清單來授予 Office 解決方案完全信任。

 最終使用者可以通過在[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示中做出信任決策來授予 Office 解決方案的信任。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>通過簽署應用程式和部署清單來信任解決方案
 Office 解決方案的所有應用程式和部署清單都必須使用標識發行者的證書進行簽名。 證書為做出信任決策提供了基礎。

 臨時證書是為您創建的，並在生成時授予信任，因此在調試解決方案時將運行解決方案。 如果發佈使用臨時證書簽名的解決方案，將提示最終使用者做出信任決策。

 如果使用已知且受信任的證書對解決方案進行簽名，則解決方案將自動安裝，而不會提示最終使用者做出信任決策。 有關如何獲取簽章憑證的詳細資訊，請參閱[ClickOnce 和身份驗證](../deployment/clickonce-and-authenticode.md)。 獲取證書後，必須通過將其添加到"受信任的發行者"清單來顯式信任該證書。 有關詳細資訊，請參閱[如何：將受信任的發行者添加到用於 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)。

 如果開發人員使用臨時證書對解決方案進行簽名，則管理員可以使用 Microsoft .NET 框架工具之一的清單生成和編輯工具 *（mage.exe）* 使用已知且受信任的證書重新對自訂進行簽名。 有關簽名解決方案的詳細資訊，請參閱[如何：對 Office 解決方案進行簽名](../vsto/how-to-sign-office-solutions.md)以及如何[：對應用程式和部署清單進行簽名](../ide/how-to-sign-application-and-deployment-manifests.md)。

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>使用 ClickOnce 信任提示信任解決方案
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]如果沒有信任解決方案證書的組織範圍策略，則提示最終使用者做出信任決策。 如果最終使用者向解決方案授予信任，則創建包含清單條目，其中包含一個 URL 和一個公開金鑰來存儲此信任決策。 稍後運行受信任的自訂項時，不會再次提示最終使用者。

 管理員可以禁用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示，或要求僅對使用身份驗證憑證簽名的解決方案執行提示。 有關如何更改"我的電腦"、"本地內聯網"、"互聯網"、"受信任的網站"和不受信任的網站區域的這些設置的詳細資訊，請參閱[：配置 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。

## <a name="see-also"></a>另請參閱

- [安全辦公室解決方案](../vsto/securing-office-solutions.md)
- [授予文檔信任](../vsto/granting-trust-to-documents.md)
- [排除 Office 解決方案安全性](../vsto/troubleshooting-office-solution-security.md)
- [Office 解決方案的特定安全注意事項](../vsto/specific-security-considerations-for-office-solutions.md)