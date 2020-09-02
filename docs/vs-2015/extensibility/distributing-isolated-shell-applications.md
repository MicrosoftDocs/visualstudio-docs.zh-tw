---
title: 散佈隔離式 Shell 應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204669"
---
# <a name="distributing-isolated-shell-applications"></a>散發獨立模式 Shell 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您必須安裝 Visual Studio 和 Visual Studio SDK，才能建立隔離式 shell 應用程式。 若要將應用程式散發給其他使用者或客戶的電腦，您必須包含獨立 shell 的特殊可轉散發套件。  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>散發隔離式 Shell 應用程式的必要條件  
  
|Name|描述|  
|----------|-----------------|  
|Visual Studio SDK|您必須具備的 SDK，才能開發和測試的擴充功能 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 您也可以使用 SDK 來建立您自己的 Visual Studio 獨立模式 shell 實例。<br /><br /> Visual Studio 是 SDK 的先決條件。|  
|Microsoft Visual Studio 獨立模式 Shell 可轉散發套件|當您在 Visual Studio 獨立模式 shell 上建立工具環境時，所包含在安裝程式中的可轉散發套件。 獨立模式 Shell 可轉散發套件包含 .NET Framework 4.5。|  
  
## <a name="creating-an-installation-program-for-the-application"></a>建立應用程式的安裝程式  
 您必須為整合式或獨立模式 shell 應用程式建立特殊的安裝程式。 如需詳細資訊，請參閱 [安裝獨立模式 Shell 應用程式](../extensibility/installing-an-isolated-shell-application.md)。  
  
## <a name="allowing-for-updates-to-your-application"></a>允許更新您的應用程式  
 您的安裝程式必須允許您的應用程式將透過 Microsoft 更新或您公司的更新進行更新。 如需更新的詳細資訊，請參閱 [獨立 Shell 應用程式的服務指導方針](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)。
