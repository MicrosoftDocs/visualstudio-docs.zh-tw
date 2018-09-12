---
title: 安全的部署
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0ed351bf15ec257f79e226958b38e46ac769d0e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35670819"
---
# <a name="secure-deployment"></a>安全的部署
  當您建立 Office 方案時，會自動允許之程式碼執行的專案中更新您的開發電腦。 不過，當您部署您的解決方案，您必須提供要簽署的憑證、 解決方案或使用根據信任決策的辨識項[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示的索引鍵。 如需詳細資訊，請參閱 <<c0> [ 授與信任給 Office 方案](../vsto/granting-trust-to-office-solutions.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 文件層級自訂中，如果文件部署到網路位置，您也必須將文件的位置加入信任中心 中的 Office 應用程式的信任位置清單。 如需如何設定在使用者電腦上的文件權限的詳細資訊，請參閱[授與信任給文件](../vsto/granting-trust-to-documents.md)。  
  
## <a name="prevent-office-solutions-from-running-code"></a>避免 Office 方案執行程式碼  
 系統管理員可以使用登錄，以防止所有的 Office 方案的電腦上執行。 具有 managed 程式碼擴充的 Office 方案開啟時，Visual Studio Tools for Office 執行階段檢查是否項目名稱`Disabled`存在於其中一種在電腦上的下列登錄機碼：  
  
-   **HKEY_CURRENT_USER\Software\Microsoft\VSTO**  
  
-   **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**  
  
 若要避免 Office 方案執行程式碼，建立`Disabled`之一或兩者的這些登錄機碼下的項目，並指定下列資料類型和值的其中一個`Disabled`:  
  
-   REG_SZ 或 REG_EXPAND_SZ 設為"0"（零） 以外的任何字串中。  
  
-   設定為 0 （零） 以外的任何值 REG_DWORD。  
  
 若要啟用 Office 方案執行程式碼，將這兩個`Disabled`項目設為 0 （零），或刪除登錄項目。  
  
## <a name="see-also"></a>另請參閱  
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [準備執行或裝載 Office 方案的電腦](http://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  