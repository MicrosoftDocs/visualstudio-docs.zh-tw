---
title: Shell （獨立模式或整合模式） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0db0ab2c2a97f7cedde5b9b3a5ab925467a25146
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300487"
---
# <a name="shell-isolated-or-integrated"></a>Shell (獨立模式或整合模式)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在整合式或隔離模式中，建立您自己的 Visual Studio 型應用程式。 在整合模式中，除了您的應用程式之外，還提供許多 Visual Studio 功能。 在獨立模式中，您可以選擇要與自己的延伸模組一起散發的 Visual Studio 功能子集。  
  
## <a name="integrated-mode"></a>整合模式  
 整合模式可讓您的使用者使用標準 Visual Studio 功能以及自訂工具。 整合式 shell 主要用於裝載程式設計語言和軟體發展工具。  
  
 內建在整合式 shell 上的自訂工具，會自動與安裝在同一部電腦上的任何其他 Visual Studio 版本合併。 如果尚未安裝 Visual Studio，您可以提供 Visual Studio 整合式 shell 的可轉散發版本。  
  
 Visual Studio 整合式 shell 的可轉散發版本不包含程式設計語言，以及支援其個別專案系統的功能。  
  
> [!NOTE]
> Visual Studio shell 整合模式可以與所有版本的 Visual Studio （Express 版本除外）一起安裝。  
  
 如需詳細資訊，請參閱[Visual Studio Shell （整合模式）](../extensibility/visual-studio-shell-integrated.md)。  
  
## <a name="isolated-mode"></a>隔離模式  
 「隔離模式」可讓您建立與其他 Visual Studio 版本並存執行的自訂工具。 它主要是用於可存取 Visual Studio 服務的工具，而不需視所有標準 Visual Studio 功能而定。 您可以自訂以 Visual Studio 獨立模式 shell 為基礎的應用程式外觀。 您可以輕鬆地關閉您不想要與應用程式一起顯示的功能和功能表命令群組。  
  
 如需詳細資訊，請參閱[Visual Studio 獨立模式 Shell](../extensibility/visual-studio-isolated-shell.md)。  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>散發您的整合式或獨立模式 Shell 應用程式  
 為了散發您的整合式或獨立模式 shell 應用程式，您必須包含應用程式、特殊的整合式或獨立 shell 可轉散發套件，以及安裝程式。 如需散發和安裝的詳細資訊，請參閱[散佈獨立模式 Shell 應用程式](../extensibility/distributing-isolated-shell-applications.md)。  
  
> [!IMPORTANT]
> Visual Studio 整合式和獨立模式 shell 的[使用者授權合約（EULA）](https://www.visualstudio.com/support/legal/mt171552)包含資料收集的章節（**第3節）。資料**）。  其中說明 Microsoft 可能會從您組建到應用程式的整合式或隔離式 shell 軟體的使用者，收集到的客戶使用資料。 如需詳細資訊，請參閱[Microsoft Visual Studio 產品系列隱私權聲明](https://www.visualstudio.com/dn948229)。  
> 
> 如果您透過應用程式向客戶收集不同的使用量資料，您必須為您所收集的應用程式使用者提供適當的通知。  當您根據 Visual Studio 軟體發展工具組授權，散發獨立或整合式 shell 軟體作為應用程式的一部分時，您必須包含下列其中一項：  
> 
> - 作為應用程式授權之一部分的使用者授權合約  
> - 您自己的 EULA，要求您的客戶同意保護 Visual Studio 整合式或隔離式 shell 的條款，至少與 shell 軟體的 Microsoft 終端使用者授權條款相同  
  
## <a name="additional-resources"></a>其他資源  
 如需可轉散發套件的詳細資訊，請參閱 Visual Studio 擴充性[下載](https://go.microsoft.com/fwlink/?LinkID=119298)網站。  
  
## <a name="see-also"></a>另請參閱  
 [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
