---
title: 如何： 設定 ClickOnce 應用程式的自訂權限 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6cf4b1c91650bf505daececfdf46ba42cfee68fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491826"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>如何：設定 ClickOnce 應用程式的自訂使用權限
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 設定 ClickOnce 應用程式的自訂權限](https://docs.microsoft.com/visualstudio/deployment/how-to-set-custom-permissions-for-a-clickonce-application)。  
  
您可以部署對網際網路或近端內部網路區域使用預設權限的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式。 或者，您可以建立應用程式所需特定權限的自訂區域。 做法是在 [專案設計工具]  的 [安全性] 頁面上自訂安全性權限。  
  
### <a name="to-customize-a-permission"></a>自訂權限  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [ **安全性** ] 索引標籤。  
  
3.  選取 [啟用 ClickOnce 安全性設定]  核取方塊。  
  
4.  選取 [這是部分信任的應用程式]  選項按鈕。  
  
     這會啟用 [ClickOnce 安全性權限]  區段中的控制項。  
  
5.  從 [安裝應用程式的區域]  下拉式清單中，按一下 [(自訂)] 。  
  
6.  按一下 [編輯權限 XML] 。  
  
     即會在 [XML 編輯器] 中開啟 app.manifest 檔案。  
  
7.  在 `</applicationRequestMinimum>` 項目之前，新增應用程式所需權限的 XML 程式碼。  
  
    > [!NOTE]
    >  您可以使用權限集的 `ToXml` 方法，產生應用程式資訊清單的 XML 程式碼。 例如，若要產生 <xref:System.Security.Permissions.EnvironmentPermission> 權限集的 XML，請呼叫 <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> 方法。 如需權限集 XML 結構的詳細資訊，請參閱 [NIB: How to: Import a Permission Set by Using an XML File](http://msdn.microsoft.com/en-us/dea16b54-c108-408a-ac36-cdc05f746236)。  
  
## <a name="see-also"></a>另請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)



