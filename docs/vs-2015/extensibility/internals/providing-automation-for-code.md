---
title: 為程式碼提供自動化 |Microsoft Docs
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
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 399900bce10edbd6fec549fc3a52ca3dbeefdabc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761556"
---
# <a name="providing-automation-for-code"></a>為程式碼提供自動化
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

建立的自動化模型，讓您的程式碼不需要。 環境 SDK 不提供這項操作的範例。 如需深入的程式碼模型，請參閱<xref:EnvDTE.CodeModel>物件。  
  
 若要實作程式碼模型，您必須實作取決於您的內部資料結構的任何介面。 物件必須衍生自`IDispatch`類別。  
  
 您擴充時，物件<xref:EnvDTE.CodeModel>並<xref:EnvDTE.FileCodeModel>，都是從<xref:EnvDTE.Project>物件，並如下所示：  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 您可以選擇實作只`CodeModel`或`FileCodeModel`介面，在您從傳回的物件您`Project`和<xref:EnvDTE.ProjectItem>物件。 提供適用於您的專案系統自此介面的任何功能。  
  
 如果您想要新增的功能，例如方法或屬性，則無法使用從標準`CodeModel`和`FileCodeModel`介面，建立您自己繼承自標準的介面。 請務必記錄與您的專案系統，讓使用者將會知道要尋找它。 傳回標準的介面，但使用者可以呼叫`QueryInterface`方法或轉型為您的介面，如果已知存在。  
  
## <a name="see-also"></a>另請參閱  
 [Automation 模型概觀](../../extensibility/internals/automation-model-overview.md)

