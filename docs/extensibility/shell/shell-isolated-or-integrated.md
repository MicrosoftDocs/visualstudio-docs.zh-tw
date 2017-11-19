---
title: "Shell （隔離或整合） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92462699141f9d0a1af2d9eb461caadf4ee467ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="shell-isolated-or-integrated"></a>Shell （隔離或整合）
您可以建立自己的 Visual Studio 為基礎應用程式中整合或隔離模式。 在整合式模式中，許多功能，Visual Studio 可用除了您的應用程式。 在隔離模式中，您可以選擇您想要發佈和您自己的擴充功能的 Visual Studio 功能的子集。  
  
## <a name="integrated-mode"></a>整合式的模式  
 整合式的模式可讓使用者在使用標準 Visual Studio 功能，以及您的自訂工具。 整合式的 shell 主要被供主控的程式設計語言和軟體開發工具。  
  
 與任何其他版本的 Visual Studio 安裝在同一部電腦上合併整合式 shell 自動建立的自訂工具。 如果尚未安裝 Visual Studio，您可以提供整合的 Visual Studio shell 的可轉散發套件版本。  
  
 Visual Studio 整合式 shell 的可轉散發套件版本不包含程式設計語言和支援個別專案系統的功能。  
  
> [!NOTE]
>  Visual Studio shell 整合的模式可以與 Visual Studio Express edition 除外的所有版本一起安裝。  
  
 如需詳細資訊，請參閱[Visual Studio Shell （整合式）](visual-studio-shell-integrated.md)。  
  
## <a name="isolated-mode"></a>隔離的模式  
 隔離的模式可讓您建立自訂的工具執行的並行與其他版本的 Visual Studio。 它主要被供可以存取 Visual Studio 服務，而不根據所有標準的 Visual Studio 功能的工具。 您可以自訂 Visual Studio isolated shell 上建置的應用程式的外觀。 您可以輕鬆地關閉您不想要顯示與您的應用程式的功能表命令群組的功能。  
  
 如需詳細資訊，請參閱[Visual Studio Isolated Shell](visual-studio-isolated-shell.md)。  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>散發應用程式整合或隔離 Shell  
 若發佈時整合或隔離 shell 應用程式，您必須包含您的應用程式、 特殊整合或隔離 shell 可轉散發套件，以及安裝程式。 如需散發與安裝的詳細資訊，請參閱[散發隔離 Shell 應用程式](distributing-isolated-shell-applications.md)。  
  
> [!IMPORTANT]
>  [終端使用者授權合約 (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) Visual Studio 整合，並隔離 shell 包含資料收集 區段 (**第 3 節。資料**)。  它會描述可能會建置您的應用程式的其中一個整合式或外掛式主控殼層軟體的使用者從由 Microsoft 所收集的客戶使用量資料。 如需詳細資訊，請參閱[Microsoft Visual Studio 產品系列隱私權聲明](https://www.visualstudio.com/en-us/dn948229)。  
>   
>  如果您收集不同的使用量資料從您的客戶透過您的應用程式，您必須提供適當通知您的收集您的應用程式的使用者。  當您將個別或整合式 shell 軟體發佈為應用程式的一部分，根據 Visual Studio 軟體開發套件的授權，您必須包含下列其中一項：  
>   
>  -   在您的應用程式授權的使用者授權合約  
> -   需要您同意條款保護 Visual Studio 的客戶自己 EULA 整合或與 Microsoft 終端使用者授權條款的殼層軟體隔離 shell 至少多  
  
## <a name="additional-resources"></a>其他資源  
 如需可轉散發套件的詳細資訊，請參閱[Visual Studio 擴充性下載](http://go.microsoft.com/fwlink/?LinkID=119298)網站。  
  
## <a name="see-also"></a>另請參閱  
 [推出 Visual Studio 擴充功能](../shipping-visual-studio-extensions.md)