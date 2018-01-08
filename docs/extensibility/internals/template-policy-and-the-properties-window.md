---
title: "原則範本和 [屬性] 視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 51735bf0f46e5a1ead6f989a8e75745ebc8e6e35
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="template-policy-and-the-properties-window"></a>原則範本和 [屬性] 視窗
專案包含企業樣板專案內的企業樣板專案可以強制執行原則。 範本的原則問題變得可用來設定屬性的預設值、 隱藏的屬性、 加入屬性等等的條件約束系統。  
  
 使用範本原則來控制顯示的資訊**屬性**視窗是不同的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>處理在元件層級的物件屬性，而範本原則可以用來限制在方案或專案層級的物件屬性。 亦即  
  
-   實作的方法上<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>來決定顯示之內容**屬性**視窗針對特定物件  
  
-   使用方案和專案層級的原則範本，來判斷中顯示的內容**屬性**先前指定之物件的視窗  
  
 選擇性地限制中的特定屬性使用樣板原則**屬性**時指定之類型的專案項目 視窗中選取**方案總管 中**可能有所助益的所有成員開發團隊使用專案。 例如，使用原則範本，您可以設定所有的連接字串資訊在資料庫中您的開發人員並將連接字串為唯讀。 如此一來，您可以提供簡單的方式，以確保每位開發人員使用正確的路徑進行資料存取。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [擴充屬性](../../extensibility/internals/extending-properties.md)