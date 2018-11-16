---
title: Shell （獨立模式或整合式） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 856e32d4569e5dcb73e783d0a6b66e186fbb1848
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755887"
---
# <a name="shell-isolated-or-integrated"></a>Shell （獨立模式或整合）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以建立自己的 Visual Studio 為基礎應用程式中整合或隔離模式。 在 整合模式中，許多 Visual Studio 功能可除了您的應用程式。 在隔離模式中，您可以選擇您想要散發和您自己的擴充功能的 Visual Studio 功能的子集。  
  
## <a name="integrated-mode"></a>整合式的模式  
 整合式的模式可讓使用者能夠使用標準的 Visual Studio 功能，以及您自訂的工具。 整合式的 shell 主要被供主控的程式設計語言與軟體開發工具。  
  
 在整合式 shell 上自動建立的自訂工具合併使用任何其他版本的 Visual Studio 安裝在同一部電腦上。 如果尚未安裝 Visual Studio，您可以提供 Visual Studio 整合式 shell 可轉散發套件版本。  
  
 Visual Studio 整合式 shell 可轉散發套件版本不包含程式設計語言和支援個別專案系統的功能。  
  
> [!NOTE]
>  Visual Studio shell 整合的模式可以與 Visual Studio Express 版本以外的所有版本一起安裝。  
  
 如需詳細資訊，請參閱 < [Visual Studio Shell （整合模式）](../extensibility/visual-studio-shell-integrated.md)。  
  
## <a name="isolated-mode"></a>隔離的模式  
 隔離的模式可讓您建立自訂執行並排顯示的工具與其他版本的 Visual Studio。 它主要被供可以存取 Visual Studio 服務，而不根據標準的 Visual Studio 功能的工具。 您可以自訂 Visual Studio isolated shell 建置的應用程式的外觀。 您可以輕鬆地關閉您不想要顯示與您的應用程式的功能表命令群組的功能。  
  
 如需詳細資訊，請參閱 < [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)。  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>散發您的整合式或外掛式 Shell 應用程式  
 若要發佈您的整合式或外掛式 shell 應用程式，您需要包括您的應用程式、 特殊整合式或外掛式 shell 可轉散發套件，以及安裝程式。 如需有關散發與安裝的詳細資訊，請參閱[散發獨立 Shell 應用程式](../extensibility/distributing-isolated-shell-applications.md)。  
  
> [!IMPORTANT]
>  [終端使用者授權合約 (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552)殼層的 Visual Studio 整合，並隔離包含資料收集 區段 (**第 3 節。資料**)。  它會描述可能會由 Microsoft 的整合式或外掛式 shell 軟體建置到您的應用程式的使用者收集的客戶使用量資料。 如需詳細資訊，請參閱 < [Microsoft Visual Studio 產品系列隱私權聲明](https://www.visualstudio.com/en-us/dn948229)。  
> 
>  如果您透過您的應用程式，從您的客戶收集不同的使用方式資料，您必須提供適當的通知給您的收集您應用程式的使用者。  當您將獨立或整合式 shell 軟體發佈為應用程式的一部分，根據 Visual Studio 軟體開發套件的授權，您必須包含下列其中一項：  
> 
> - 使用者授權合約，為您的應用程式授權的一部分  
>   -   需要您的客戶同意保護 Visual Studio 的條款自己使用者授權合約或整合獨立模式 shell 的程度，為 Microsoft 使用者授權條款，shell 軟體  
  
## <a name="additional-resources"></a>其他資源  
 如需有關可轉散發套件的詳細資訊，請參閱[Visual Studio 擴充性下載](http://go.microsoft.com/fwlink/?LinkID=119298)網站。  
  
## <a name="see-also"></a>另請參閱  
 [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)

