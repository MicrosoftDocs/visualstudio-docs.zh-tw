---
title: 如何： 啟用 ClickOnce 安全性設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc3f87e590c6b915d5b3d9db5d2517d80965dd6c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558616"
---
# <a name="how-to-enable-clickonce-security-settings"></a>How to: Enable ClickOnce Security Settings
必須啟用 ClickOnce 應用程式的程式碼存取安全性，才能發行應用程式。 當您發行應用程式使用發行精靈時，這會自動完成。  
  
 在某些情況下，在啟用程式碼存取安全性會影響效能，當建置或偵錯您的應用程式;在這些情況下，您可能想要暫時停用的安全性設定。  
  
 您可以啟用或停用 ClickOnce 安全性設定**安全性**頁面**專案設計工具**。  
  
### <a name="to-enable-clickonce-security-settings"></a>若要啟用 ClickOnce 安全性設定  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [ **安全性** ] 索引標籤。  
  
3.  選取 [啟用 ClickOnce 安全性設定]  核取方塊。  
  
     您現在可以在 [安全性] 頁面上的應用程式自訂的安全性設定。  
  
    > [!NOTE]
    >  此核取方塊會自動選取以發行應用程式每次**發行**精靈。  
  
### <a name="to-disable-clickonce-security-settings"></a>若要停用 ClickOnce 安全性設定  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [ **安全性** ] 索引標籤。  
  
3.  清除**啟用 ClickOnce 安全性設定**核取方塊。  
  
     您的應用程式將會執行完全信任的安全性設定。上的任何設定**安全性**頁面將會被忽略。  
  
    > [!NOTE]
    >  使用發行精靈發行應用程式每次會選取此核取方塊。您必須將它清除每個成功發佈之後，再次。  
  
## <a name="see-also"></a>另請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 
