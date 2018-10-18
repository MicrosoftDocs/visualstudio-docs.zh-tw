---
title: 如何： 偵錯部分信任應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b3b7bb7e880b30e975770ee35dfb537e62827b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288219"
---
# <a name="how-to-debug-a-partial-trust-application"></a>How to: Debug a Partial Trust Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

適用於 Windows 和主控台應用程式。  
  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)輕鬆地部署部分信任應用程式，善用[程式碼存取安全性](http://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127)限制存取權的電腦上的資源。  
  
 偵錯部分信任的應用程式頗具挑戰性，因為根據進行安裝的來源位置不同，部分信任的應用程式也會有不同的安全性權限 (因此行為也不同)。 如果是從網際網路進行安裝，則部分信任的應用程式會具有較少使用權限。 如果是從近端內部網路進行安裝，則會擁有較多的使用權限。如果是從本機電腦進行安裝，則具有完整的使用權限  您可能也擁有自訂區域，這會具有自訂使用權限。 您可能必須在上述任何或所有條件下，才能偵錯部分信任的應用程式。 幸運的是，Visual Studio 也能讓這類偵錯變得更簡單。  
  
 在 Visual Studio 中啟動偵錯工作階段之前，您必須選擇要模擬為應用程式安裝來源的區域。 當您啟動偵錯時，應用程式會擁有從該區域安裝之部分信任的應用程式所適用的使用權限。 這能讓您看見應用程式的行為，這些行為會與從該區域下載該應用程式的使用者所見的一樣。  
  
 如果應用程式嘗試執行其沒有使用權限的動作，就會發生例外狀況。 這時，例外狀況助理會提供您加入額外使用權限的機會，允許您使用足夠的使用權限重新啟動偵錯工作階段，以避免這個問題。  
  
 稍候，您可以在偵錯期間返回並查看您加入了那些使用權限。 如果您在偵錯期間加入使用權限，可能會立刻指出您必須在程式碼中加入使用者同意提示。  
  
> [!NOTE]
>  偵錯工具視覺化檢視需要比部分信任應用程式所允許還要大的權限。 當您在部分信任的程式碼中被停止時，視覺化檢視將不會載入。 若要使用視覺化檢視進行偵錯，您必須以完全信任方式執行程式碼。  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>若要選擇部分信任應用程式的區域  
  
1.  從**專案**功能表上，選擇_Projectname_**屬性**。  
  
2.  在  *Projectname*  屬性頁面上，按一下 **安全性**頁面。  
  
3.  選取 **啟用 ClickOnce 安全性設定**。  
  
4.  底下**從安裝應用程式的區域**、 按一下下拉式清單方塊，然後選擇您想要模擬安裝應用程式的區域。  
  
     **應用程式所需的權限**方格會顯示所有可用的權限。 核取記號會指出已授與應用程式的使用權限。  
  
5.  如果您選擇的區域 **（自訂）**，選取正確的自訂設定，在**設定**資料行**權限**方格。  
  
6.  按一下 [確定] 關閉屬性頁。  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>若要在發生安全性例外狀況時加入額外使用權限  
  
1.  **例外狀況助理** 對話方塊隨即出現並顯示訊息： **SecurityException 未處理。**  
  
2.  在 **例外狀況助理**對話方塊的 **動作**，按一下 **新增至專案的權限**。  
  
3.  **重新啟動偵錯** 對話方塊隨即出現。  
  
    -   如果您想要重新啟動新的權限的偵錯工作階段，請按一下**是**。  
  
    -   如果您不想要重新啟動，請按一下**No**。  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>若要在偵錯期間檢視已加入的額外使用權限  
  
1.  從**專案**功能表上，選擇_Projectname_**屬性**。  
  
2.  在  *Projectname*  屬性頁面上，按一下 **安全性**頁面。  
  
3.  看看**應用程式所需的權限**方格。 您新增任何額外使用權限中有兩個圖示**包含**資料行： 的正常核取記號，所有已納入的擁有權限，這與其他圖示，如下所示包含字母"i"的汽球。  
  
4.  用於垂直捲軸檢視整個**應用程式所需的權限**方格。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)



