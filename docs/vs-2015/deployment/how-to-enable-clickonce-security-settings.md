---
title: 如何： 啟用 ClickOnce 安全性設定 |Microsoft Docs
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
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 65cba913afdee2379e5f702dda460cea2a33598f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487064"
---
# <a name="how-to-enable-clickonce-security-settings"></a>How to: Enable ClickOnce Security Settings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 啟用 ClickOnce 安全性設定](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-clickonce-security-settings)。  
  
為了發佈應用程式，就必須啟用程式碼存取安全性，ClickOnce 應用程式。 當您發行應用程式使用發佈精靈時，這會自動完成。  
  
 在某些情況下，啟用程式碼存取安全性可能會影響效能時建置或偵錯您的應用程式;在這些情況下，您可能想要暫時停用的安全性設定。  
  
 ClickOnce 安全性設定可以啟用或停用**安全性**頁**專案設計工具**。  
  
### <a name="to-enable-clickonce-security-settings"></a>若要啟用 ClickOnce 安全性設定  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [ **安全性** ] 索引標籤。  
  
3.  選取 [啟用 ClickOnce 安全性設定]  核取方塊。  
  
     您現在可以在 [安全性] 頁面上的應用程式自訂的安全性設定。  
  
    > [!NOTE]
    >  此核取方塊會自動選取以發行應用程式每次**發佈**精靈。  
  
### <a name="to-disable-clickonce-security-settings"></a>若要停用 ClickOnce 安全性設定  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [ **安全性** ] 索引標籤。  
  
3.  清除**啟用 ClickOnce 安全性設定**核取方塊。  
  
     您的應用程式將會執行完全信任的安全性設定;上的任何設定**安全性**頁面將會被忽略。  
  
    > [!NOTE]
    >  使用 [發行精靈] 中，發行應用程式每次會選取此核取方塊;您必須在每次成功的發行之後，再次加以清除。  
  
## <a name="see-also"></a>另請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)



