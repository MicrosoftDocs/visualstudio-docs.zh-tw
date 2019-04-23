---
title: 服務 Essentials |Microsoft Docs
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
ms.openlocfilehash: 5b659560c7242fa691fe046b5e1628b1e47c2a2d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111594"
---
# <a name="service-essentials"></a>服務的基本資訊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

服務是兩個的 Vspackage 之間的合約。 一個 VSPackage 提供一組特定的介面使用的另一個 VSPackage。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 本身是提供服務給其他 Vspackage 的 Vspackage 集合。  
  
 例如，您可以使用 SVsActivityLog 服務取得 IVsActivityLog 介面，可用來寫入活動記錄檔。 如需詳細資訊，請參閱[如何：使用活動記錄](../../extensibility/how-to-use-the-activity-log.md)。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 也提供一些內建的服務未註冊的。 Vspackage 可以藉由提供服務的覆寫來取代內建或其他服務。 只有一個服務覆寫所允許的任何服務。  
  
 服務有沒有可測知性。 因此，您必須知道您想要使用的服務的服務識別碼 (SID)，而且您必須知道它所提供的介面。 服務的參考文件提供這項資訊。  
  
- 提供服務的 Vspackage 會呼叫服務提供者。  
  
- 其他 vspackage 提供的服務稱為 「 全域服務 」。  
  
- 僅適用於 VSPackage 實作它們，或它所建立的任何物件，會呼叫本機服務的服務。  
  
- 取代內建的服務或由其他套件，提供服務的服務稱為服務覆寫。  
  
- 視需要載入服務或服務的覆寫，另一個 VSPackage 要求它所提供的服務時，也就是載入服務提供者。  
  
- 若要支援依需求載入，服務提供者註冊其全域服務與[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 登錄服務](../../misc/registering-services.md)。  
  
- 取得服務之後，請使用[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (unmanaged 程式碼) 或轉型 （managed 程式碼） 來取得所需的介面，例如：  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- Managed 程式碼是指服務依其型別，而未受管理的程式碼係指服務的 GUID 來。  
  
- 當[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]VSPackage 的載入，就會傳遞服務提供者至 VSPackage 的 VSPackage 的存取權給予全域服務。 這稱為 「 地點 」 VSPackage。  
  
- Vspackage 可以是服務提供者所建立的物件。 例如，表單可能會傳送色彩服務的要求至其的框架，可能會傳遞要求[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
- 受管理的物件深度巢狀，或未設置，可能會呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>全域服務的直接存取。 如需詳細資訊，請參閱[如何：使用 GetGlobalService](../../misc/how-to-use-getglobalservice.md)。  
  
## <a name="see-also"></a>另請參閱  
 [可用服務清單](../../extensibility/internals/list-of-available-services.md)   
 [使用和提供服務](../../extensibility/using-and-providing-services.md)   
 [轉型和類型轉換](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [轉型](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
