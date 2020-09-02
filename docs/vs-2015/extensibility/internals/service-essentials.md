---
title: 服務基本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696073"
---
# <a name="service-essentials"></a>服務的基本資訊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

服務是兩個 Vspackage 之間的合約。 其中一個 VSPackage 會提供一組特定的介面，供另一個要取用的 VSPackage 使用。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 本身是提供服務給其他 Vspackage 的 Vspackage 集合。  
  
 例如，您可以使用 SVsActivityLog 服務取得 IVsActivityLog 介面，此介面可用來寫入活動記錄。 如需詳細資訊，請參閱 [如何：使用活動記錄](../../extensibility/how-to-use-the-activity-log.md)。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 也提供一些未註冊的內建服務。 Vspackage 可以藉由提供服務覆寫來取代內建或其他服務。 任何服務都只允許一個服務覆寫。  
  
 服務沒有可搜尋的。 因此，您必須知道您想要取用之服務的服務識別碼 (SID) ，而且必須知道它所提供的介面。 服務的參考檔會提供此資訊。  
  
- 提供服務的 Vspackage 稱為服務提供者。  
  
- 提供給其他 Vspackage 的服務稱為「全域服務」。  
  
- 只有執行這些服務的 VSPackage 或其所建立的任何物件才能使用這些服務，稱為本機服務。  
  
- 取代其他封裝所提供的內建服務或服務的服務，稱為服務覆寫。  
  
- 服務或服務覆寫會視需要載入，也就是當另一個 VSPackage 要求服務提供者所提供的服務時，就會載入服務提供者。  
  
- 為了支援隨選載入，服務提供者會向註冊其全域服務 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱 [註冊服務](../../misc/registering-services.md)。  
  
- 取得服務之後，請使用 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (非受控程式碼) 或轉換 (managed 程式碼) 以取得所需的介面，例如：  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- Managed 程式碼是由其型別所參考的服務，而非受控碼則是透過其 GUID 來參考服務。  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]載入 VSPackage 時，它會將服務提供者傳遞給 VSPackage，以授與 VSPackage 對全域服務的存取權。 這稱為「地點」 VSPackage。  
  
- Vspackage 可以是其所建立物件的服務提供者。 例如，表單可能會將色彩服務的要求傳送至其框架，而這可能會將要求傳遞至 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
- 具有深層嵌套或未放置的 Managed 物件，可能會呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 以直接存取全域服務。 如需詳細資訊，請參閱 [如何：使用 GetGlobalService](../../misc/how-to-use-getglobalservice.md)。  
  
## <a name="see-also"></a>另請參閱  
 [可用服務的清單](../../extensibility/internals/list-of-available-services.md)   
 [使用和提供服務](../../extensibility/using-and-providing-services.md)   
 [轉換和類型轉換](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [轉型](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
