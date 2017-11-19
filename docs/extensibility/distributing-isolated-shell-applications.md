---
redirect_url: shell/distributing-isolated-shell-applications
title: "散發 Isolated 的 Shell 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a40d2b8c108d7180ffc68ac2eee6811d49b21c08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="distributing-isolated-shell-applications"></a>散發 Isolated 的 Shell 應用程式
若要建立獨立的 shell 應用程式，您必須安裝 Visual Studio 和 Visual Studio SDK。 散發到電腦其他使用者或客戶的應用程式，必須包含在 isolated shell 的特殊可轉散發套件。  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>散發 Isolated 的 Shell 應用程式的必要條件  
  
|名稱|說明|  
|----------|-----------------|  
|Visual Studio SDK|您必須以開發並測試的擴充功能 SDK [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 您也可以使用 SDK 來建立您自己的 Visual Studio isolated shell 的執行個體。<br /><br /> Visual Studio 是 SDK 的必要條件。|  
|Microsoft Visual Studio Isolated Shell 可轉散發套件|可轉散發套件您包含安裝程式中，當您建置在 Visual Studio 工具環境隔離 shell。 隔離的 Shell 可轉散發套件包含.NET Framework 4.5。|  
  
## <a name="creating-an-installation-program-for-the-application"></a>建立應用程式的安裝程式  
 您必須建立特殊的安裝程式的整合式或外掛式主控 shell 應用程式。 如需詳細資訊，請參閱[安裝獨立 Shell 應用程式](../extensibility/installing-an-isolated-shell-application.md)。  
  
## <a name="allowing-for-updates-to-your-application"></a>允許您的應用程式的更新  
 您的安裝程式必須允許，您的應用程式都會更新，Microsoft 更新或貴公司的更新的可能性。 如需有關更新的詳細資訊，請參閱[服務隔離 Shell 應用程式的指導方針](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)。