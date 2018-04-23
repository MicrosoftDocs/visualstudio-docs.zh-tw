---
title: 提供程式碼的自動化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f9dbb7a8ddad39f01f5b29443168eebe12a2da8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="providing-automation-for-code"></a>提供程式碼的自動化
建立 automation 模型，讓您的程式碼不需要。 環境 SDK 不這麼做提供範例。 如需深入的程式碼模型，請參閱<xref:EnvDTE.CodeModel>物件。  
  
 若要實作程式碼模型，您必須實作取決於您的內部資料結構的任何介面。 物件必須衍生自`IDispatch`類別。  
  
 物件，其延伸，<xref:EnvDTE.CodeModel>和<xref:EnvDTE.FileCodeModel>，都是從<xref:EnvDTE.Project>物件，並如下所示：  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 您可以選擇實作只`CodeModel`或`FileCodeModel`介面從傳回的物件中您`Project`和<xref:EnvDTE.ProjectItem>物件。 提供適用於您的專案系統自此介面的任何功能。  
  
 如果您想要新增的功能，例如方法或屬性，不提供從標準`CodeModel`和`FileCodeModel`介面，建立您自己繼承自標準的介面。 請務必記錄與您的專案系統，讓使用者將會知道要尋找它。 傳回標準的介面，但使用者可以呼叫`QueryInterface`方法或轉型，如果它已存在於您的介面。  
  
## <a name="see-also"></a>另請參閱  
 [Automation 模型概觀](../../extensibility/internals/automation-model-overview.md)