---
title: 部署 Office 方案
description: 您可以使用 ClickOnce 或 Windows Installer 部署 Office 方案。 藉由使用 ClickOnce，您可以減少部署解決方案所需的步驟數目。
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e10e922e346dc2ff1d289de94b398b7afd8f3f18
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846307"
---
# <a name="deploy-an-office-solution"></a>部署 Office 方案
  您可以使用 ClickOnce 或 Windows Installer 部署 Office 方案。 使用 ClickOnce 可減少部署和更新您的方案所需的步驟。 如果您使用 Windows Installer，就可以控制安裝方案的方式，以及使用者安裝您的方案時安裝程式顯示的頁面。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>使用 ClickOnce 部署方案
 當您使用 ClickOnce 部署方案時，會將方案發行至可供使用者安裝及執行的中央位置。 您可以更新方案，而不必將新的安裝程式散發給使用者。  這個部署選項比較簡單，不過，您無法對使用者顯示自訂設定頁面。 此外，方案必須在擁有多位使用者的所有電腦上安裝多次。 請參閱 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。

## <a name="deploy-a-solution-by-using-windows-installer"></a>使用 Windows Installer 部署解決方案
 當您使用 Windows Installer 部署方案時，會將安裝程式散發給使用者，而使用者會使用該程式安裝方案。 安裝程式可以同時為電腦的所有使用者安裝方案，而不只是目前使用者。 您還能夠透過在使用者安裝方案時顯示的選項掌控更多方面。 例如，您可以顯示授權合約或是讓使用者安裝方案的特定元件。 不過，如果您更新方案，就必須散發新的安裝程式。 請參閱 [使用 Windows Installer 部署 Office 方案](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)。

## <a name="see-also"></a>另請參閱
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [使用 Windows Installer 部署 Office 方案](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)
- [針對 Office 方案部署進行疑難排解](../vsto/troubleshooting-office-solution-deployment.md)
