---
title: 散發 Isolated 的 Shell 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7388a5b723b5346f1f653024215c16ba474fa48a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498938"
---
# <a name="distributing-isolated-shell-applications"></a>散發 Isolated 的 Shell 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[散發獨立 Shell 應用程式](https://docs.microsoft.com/visualstudio/extensibility/distributing-isolated-shell-applications)。  
  
您必須安裝 Visual Studio 和 Visual Studio SDK，才能建立 isolated 的 shell 應用程式。 若要散發到電腦的其他使用者或客戶的應用程式，您必須包含特殊 isolated shell 可轉散發套件。  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>散發 Isolated 的 Shell 應用程式的必要條件  
  
|名稱|描述|  
|----------|-----------------|  
|Visual Studio SDK|您必須開發和測試的擴充功能 SDK [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 您也可以使用 SDK 來建立您自己的 Visual Studio 隔離 shell 執行個體。<br /><br /> Visual Studio 是 SDK 的必要條件。|  
|Microsoft Visual Studio 獨立模式 Shell 可轉散發套件|可轉散發套件建置在 Visual Studio 工具環境時，包含您的安裝程式在獨立模式 shell。 獨立模式的 Shell 可轉散發套件包含.NET Framework 4.5。|  
  
## <a name="creating-an-installation-program-for-the-application"></a>建立應用程式的安裝程式  
 整合式或外掛式 shell 應用程式，您必須建立特殊的安裝程式。 如需詳細資訊，請參閱 <<c0> [ 安裝獨立 Shell 應用程式](../extensibility/installing-an-isolated-shell-application.md)。  
  
## <a name="allowing-for-updates-to-your-application"></a>可讓您的應用程式的更新  
 您的安裝程式必須允許，您的應用程式將會更新，Microsoft 更新或貴公司的更新的可能性。 如需有關更新的詳細資訊，請參閱 <<c0> [ 獨立 Shell 應用程式服務方針](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)。

