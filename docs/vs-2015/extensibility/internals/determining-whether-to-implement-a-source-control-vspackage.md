---
title: 決定是否要實作原始檔控制 VSPackage |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2af76d97b9fcf725079593155f8c3c5f695ca50a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497502"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>決定是否要實作原始檔控制 VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[決定是否要實作原始檔控制 VSPackage](https://docs.microsoft.com/visualstudio/extensibility/internals/determining-whether-to-implement-a-source-control-vspackage)。  
  
本節中，將詳細說明選擇原始檔控制外掛程式和原始檔控制 Vspackage 擴充原始檔控制解決方案，並提供廣泛的指導方針選擇適合整合路徑的相關。  
  
## <a name="small-source-control-solution-with-limited-resources"></a>資源有限的小型的原始檔控制解決方案  
 如果您具有有限的資源，而且無法負擔寫入原始檔控制封裝的額外負荷，您可以建立原始檔控制外掛程式 API 為基礎的外掛程式。這可讓您與原始檔控制套件，並存運作，您可以將其切換原始檔控制外掛程式和隨選的封裝。 如需詳細資訊，請參閱 <<c0> [ 註冊和選取](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>大型的原始檔控制解決方案，使用一組豐富的功能  
 如果您想要實作提供豐富的原始檔控制模型未充分利用原始檔控制外掛程式 API 擷取原始檔控制解決方案，您可以考慮原始檔控制套件做為整合路徑。 這適用於而是會取代原始檔控制配接器套件 （其會與原始檔控制外掛程式進行通訊，提供基本的原始檔控制 UI） 時，尤其以您自己，好讓您可以自訂的方式處理的來源控制項事件。 如果您已經有令人滿意的原始檔控制 UI，並且想要保留在該體驗[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，原始檔控制封裝選項可讓您執行上述工作。 原始檔控制套件不是泛型，而且是僅供搭配[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE。  
  
 如果您想要實作原始檔控制解決方案，可提供彈性和更能控制的原始檔控制邏輯和 UI，您可能偏好的原始檔控制套件整合路由。 您可以：  
  
1.  註冊您自己的原始檔控制 VSPackage (請參閱[註冊和選取](../../extensibility/internals/registration-and-selection-source-control-vspackage.md))。  
  
2.  您的自訂 UI 以取代預設原始檔控制 UI (請參閱[自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md))。  
  
3.  指定要使用，並處理方案總管 中的圖像 （glyph） 事件的圖像 （glyph） (請參閱[字符控制](../../extensibility/internals/glyph-control-source-control-vspackage.md))。  
  
4.  處理查詢編輯並查詢儲存的事件 (請參閱[查詢編輯查詢儲存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md))。  
  
## <a name="see-also"></a>另請參閱  
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)

