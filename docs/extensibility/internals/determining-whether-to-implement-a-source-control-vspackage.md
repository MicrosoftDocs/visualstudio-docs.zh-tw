---
title: 決定是否要實作原始檔控制 VSPackage |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 88281496c2e8350f910feda7934e2b55a494243b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>決定是否要實作原始檔控制 VSPackage
本節的擴充原始檔控制方案並提供廣泛的指導方針選擇適合整合路徑的相關 elaborates 的原始檔控制外掛程式和原始檔控制 Vspackage 的選擇。  
  
## <a name="small-source-control-solution-with-limited-resources"></a>有限資源小型的原始檔控制方案  
 如果您具有有限的資源，並無法寫入原始檔控制封裝的額外負荷負擔，您可以建立原始檔控制外掛程式 API 為基礎的外掛程式。這可讓您能夠與原始檔控制套件，並切換原始檔控制外掛程式和隨選的封裝。 如需詳細資訊，請參閱[註冊和選取範圍](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>大型的原始檔控制方案豐富功能集  
 如果您想要實作提供豐富的原始檔控制模型未充分利用原始檔控制外掛程式 API 擷取原始檔控制方案，您可以考慮原始檔控制封裝做為整合路徑。 這適用於尤其而是會取代原始檔控制配接器套件 （其與原始檔控制外掛程式通訊，提供基本的原始檔控制 UI） 以您自己，好讓您可以自訂方式來處理來源控制項事件。 如果您已經有令人滿意的原始檔控制 UI，並想要保留在該經驗[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，原始檔控制封裝選項可讓您執行上述工作。 原始檔控制封裝不是泛型，且只適用於與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 如果您想要實作提供彈性和更豐富的控制力的原始檔控制邏輯和 UI 原始檔控制方案，您可能會偏好的原始檔控制封裝整合路由。 您可以：  
  
1.  註冊您自己的原始檔控制 VSPackage (請參閱[註冊和選取範圍](../../extensibility/internals/registration-and-selection-source-control-vspackage.md))。  
  
2.  自訂 UI 以取代預設原始檔控制 UI (請參閱[自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md))。  
  
3.  指定使用和處理方案總管 中字符事件圖像 (請參閱[圖像控制項](../../extensibility/internals/glyph-control-source-control-vspackage.md))。  
  
4.  處理查詢編輯和儲存查詢的事件 (請參閱[查詢編輯查詢儲存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md))。  
  
## <a name="see-also"></a>請參閱  
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)