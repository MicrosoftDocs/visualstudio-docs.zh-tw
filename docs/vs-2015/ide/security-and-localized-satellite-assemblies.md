---
title: 安全性和當地語系化附屬組件 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d817569a5f6709794b452fb5efe38d584669033f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218643"
---
# <a name="security-and-localized-satellite-assemblies"></a>安全性和當地語系化附屬組件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您的主要組件使用強式命名，則必須使用與主要組件相同的私密金鑰來簽署附屬組件。 如果主要與附屬組件的公開/私密金鑰組不符，則不會載入資源。 如需簽署組件的詳細資訊，請參閱[如何：使用強式名稱簽署組件](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)。  
  
 一般而言，您可能需要讓組織的簽署群組或外部簽署組織使用私密金鑰進行簽署。 原因是私密金鑰具有機密本質︰通常只有少數人才能進行存取。 您可以在開發期間使用延遲簽署。 如需詳細資訊，請參閱[延遲簽署組件](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070)。  
  
## <a name="see-also"></a>另請參閱  
 [組件安全性考量](http://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [重要的安全性概念](http://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [以 .NET Framework 為基礎的國際應用程式簡介](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [當地語系化應用程式](../ide/localizing-applications.md)   
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)

