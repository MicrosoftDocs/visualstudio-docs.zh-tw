---
title: 如何：啟用 ClickOnce 安全性設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1b104a7a0451da7f772077d2f566b36b9f601c17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838906"
---
# <a name="how-to-enable-clickonce-security-settings"></a>How to: Enable ClickOnce Security Settings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您必須啟用 ClickOnce 應用程式的代碼啟用安全性，才能發佈應用程式。 當您使用 [發佈嚮導] 發行應用程式時，就會自動完成這項操作。  
  
 在某些情況下，啟用代碼啟用安全性可能會在建立或偵錯工具時影響效能;在這些情況下，您可能會想要暫時停用安全性設定。  
  
 您可以在 [**專案設計**工具] 的 [**安全性**] 頁面上啟用或停用 ClickOnce 安全性設定。  
  
### <a name="to-enable-clickonce-security-settings"></a>啟用 ClickOnce 安全性設定  
  
1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。  
  
2. 按一下 [安全性] 索引標籤。  
  
3. 選取 [啟用 ClickOnce 安全性設定] **** 核取方塊。  
  
     您現在可以在 [安全性] 頁面上自訂應用程式的安全性設定。  
  
    > [!NOTE]
    > 每次使用 [ **發佈** 嚮導] 發行應用程式時，就會自動選取此核取方塊。  
  
### <a name="to-disable-clickonce-security-settings"></a>停用 ClickOnce 安全性設定  
  
1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。  
  
2. 按一下 [安全性] 索引標籤。  
  
3. 清除 [ **啟用 ClickOnce 安全性設定** ] 核取方塊。  
  
     您的應用程式將會以完全信任安全性設定執行; **安全性** 頁面上的任何設定都會被忽略。  
  
    > [!NOTE]
    > 每次使用 [發佈嚮導] 發行應用程式時，就會選取此核取方塊;您必須在每次成功發佈之後再次將它清除。  
  
## <a name="see-also"></a>另請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的代碼啟用安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
