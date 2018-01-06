---
title: "如何： 在 ClickOnce 應用程式中納入資料檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a7ddfdb0518a8e3154d966fdea884bf7f2e3ea37
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>How to: Include a Data File in a ClickOnce Application
每個[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]您安裝的應用程式指派應用程式可在其中管理它自己的資料的目的地電腦的本機磁碟上的資料目錄。 資料檔案可以包含任何類型的檔案： 文字檔、 XML 檔案或甚至是 Microsoft Access 資料庫 (.mdb) 檔案。 下列程序說明如何新增至任何類型的資料檔您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>若要使用 Mage.exe 納入資料檔案  
  
1.  將資料檔加入至您的應用程式檔案的其餘部分的應用程式目錄。  
  
     一般而言，應用程式目錄都將標示為與部署的目前版本的目錄，例如 v1.0.0.0。  
  
2.  更新清單的資料檔案的應用程式資訊清單。  
  
     **mage-u v1.0.0.0\Application.manifest-FromDirectory v1.0.0.0**  
  
     執行此工作會重新建立您的應用程式資訊清單中的檔案清單，也會自動產生的雜湊簽章。  
  
3.  在您慣用的文字或 XML 編輯器中開啟應用程式資訊清單，並尋找`file`您最近加入的檔案項目。  
  
     如果您加入名為 XML 檔案`Data.xml`，檔案看起來類似下列的程式碼範例。  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  將屬性加入`type`至這個項目，並提供其值為`data`。  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  重新簽署應用程式資訊清單使用您的金鑰組或憑證，並重新簽署部署資訊清單。  
  
     您必須重新簽署部署資訊清單，因為它的應用程式資訊清單的雜湊已變更。  
  
     **mage-s 應用程式資訊清單-cf cert_file-pwd 密碼**  
  
     **mage-u 部署資訊清單 appm 應用程式資訊清單**  
  
     **mage-s 部署資訊清單-cf certfile-pwd 密碼**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>若要使用 MageUI.exe 中納入資料檔案  
  
1.  將資料檔加入至您的應用程式檔案的其餘部分的應用程式目錄。  
  
2.  一般而言，應用程式目錄都將標示為與部署的目前版本的目錄，例如 v1.0.0.0。  
  
3.  在**檔案**功能表上，按一下 **開啟**開啟應用程式資訊清單。  
  
4.  選取**檔案** 索引標籤。  
  
5.  在 [] 索引標籤頂端的文字方塊中輸入包含您的應用程式檔案的目錄，然後按一下**填入**。  
  
     您的資料檔案會出現在方格中。  
  
6.  設定**檔案類型**值的資料檔**資料**。  
  
7.  儲存應用程式資訊清單，並重新簽署檔案。  
  
     MageUI.exe 會提示您重新簽署檔案。  
  
8.  重新簽署部署資訊清單  
  
     您必須重新簽署部署資訊清單，因為它的應用程式資訊清單的雜湊已變更。  
  
## <a name="see-also"></a>請參閱  
 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)