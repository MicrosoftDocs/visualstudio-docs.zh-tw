---
title: 管理組件和資訊清單簽署 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 45bd0720bfd16be2266bbdb56e962d1744ebbf84
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674864"
---
# <a name="managing-assembly-and-manifest-signing"></a>管理組件和資訊清單簽署
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

強式名稱簽署提供軟體元件的全域唯一識別。 強式名稱用以保證組件無法為他人作為詐騙之用，並確保元件的相依性和組態陳述式會對應到正確的元件和元件版本。  
  
 強式名稱是由組件的身分識別 (簡單文字名稱、版本號碼及文化特性資訊)，加上公開金鑰語彙基元和數位簽章所組成。  
  
 如需 Visual Basic 和 C# 專案中簽署組件的資訊，請參閱[建立和使用強式名稱的組件](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9)。  
  
 如需 Visual C++ 專案中簽署組件的資訊，請參閱[強式名稱組件 (組件簽署) (C++/CLI)](https://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)。  
  
## <a name="asset-types-and-signing"></a>資產類型和簽章  
 您可以簽署 .NET 組件和應用程式資訊清單。 這些需求包括下列各項：  
  
- 可執行檔 (.exe)  
  
- 應用程式資訊清單 (.exe.manifest)  
  
- 部署資訊清單 (.application)  
  
- 共用的元件組件 (.dll)  
  
  您必須登入下列資產類型︰  
  
1. 組件，如果您想要將它們部署到全域組件快取 (GAC)。  
  
2. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式和部署資訊清單。 Visual Studio 根據預設可簽署這些應用程式。  
  
3. 主要 Interop 組件，用於 COM 互通性。 從 COM 類型程式庫建立主要 Interop 組件時，TLBIMP 公用程式會強制執行強式命名。  
  
   通常，您不應該簽署可執行檔。 強式名稱元件無法參考與應用程式一起部署的非強式名稱元件。 Visual Studio 不簽署應用程式可執行檔，而是改為簽署應用程式資訊清單，指向弱式命名的可執行檔。 通常，您應該避免簽署應用程式的私用元件，因為簽章會使得相依性更難以管理。  
  
## <a name="how-to-sign-an-assembly-in-visual-studio"></a>如何簽署 Visual Studio 中的組件  
 使用專案 [專案屬性] 視窗的 [簽署] 索引標籤來簽署應用程式或元件 (以滑鼠右鍵按一下方案總管中的專案節點 ，然後選取 [屬性]，或在 [快速啟動] 視窗中鍵入**專案屬性**，或在方案總管視窗中按 ALT + ENTER)。 選取 [簽署] 索引標籤，然後選取 [簽署組件] 核取方塊。  
  
 指定金鑰檔。 如果您選擇建立新的金鑰檔，請注意新的金鑰檔一律使用 .pfx 格式建立。 您需要新檔案的名稱和密碼。  
  
> [!WARNING]
> 您應該一律以密碼保護金鑰檔，以防止他人使用您的金鑰檔。 您也可以使用提供者或憑證存放區來保護您的金鑰。  
  
 您也可以指向已經建立的金錀。 如需建立金鑰的詳細資訊，請參閱[如何：建立公用/私密金鑰組](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)。  
  
 如果您只能存取公開金鑰，您可以使用延遲簽署，稍後再指定金鑰。 選取 [僅延遲簽署] 核取方塊以啟用延遲簽署。 延遲簽署的專案將不會執行，且無法進行偵錯。 不過，您可以在開發期間略過驗證，使用 [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) 與 `-Vr` 選項。  
  
 如需簽署資訊清單的資訊，請參閱[如何：簽署應用程式和部署資訊清單](../ide/how-to-sign-application-and-deployment-manifests.md)。  
  
## <a name="see-also"></a>請參閱  
 [強式名稱的組件](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [強式名稱組件 (組件簽署) (C++/CLI)](https://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)
