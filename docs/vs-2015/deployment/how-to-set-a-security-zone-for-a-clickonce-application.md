---
title: 如何：設定 ClickOnce 應用程式的安全性區域 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9af4507d7ccd604f82aae675bf87d36c0b039b26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68171426"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>How to: Set a Security Zone for a ClickOnce Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

設定 ClickOnce 應用程式的程式碼存取安全性權限時，必須從 [專案設計工具] **** 之 [安全性] **** 頁面上的一組基底權限開始。  
  
 在大多數情況下，您也可以選擇 [網際網路] **** 區域 (包含一組有限的權限) 或 [近端內部網路] **** 區域 (包含一組更高的權限)。 如果應用程式需要自訂權限，您可以選擇 [自訂] **** 安全性區域來完成。 如需設定自訂權限的詳細資訊，請參閱 [如何：設定 ClickOnce 應用程式的自訂使用權限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)。  
  
### <a name="to-set-a-security-zone"></a>設定安全性區域  
  
1. 在 **方案總管**中選取專案時，在 [ **專案** ] 功能表上按一下 [ **屬性**]。  
  
2. 按一下 [安全性] 索引標籤。  
  
3. 選取 [啟用 ClickOnce 安全性設定] **** 核取方塊。  
  
4. 選取 [這是部分信任的應用程式] **** 選項按鈕。  
  
     這會啟用 [ClickOnce 安全性權限] **** 區段中的控制項。  
  
5. 在 [安裝應用程式的區域] **** 下拉式清單中，選取安全性區域。  
  
## <a name="see-also"></a>另請參閱  
 [如何：設定 ClickOnce 應用程式的自訂許可權](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的代碼啟用安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
