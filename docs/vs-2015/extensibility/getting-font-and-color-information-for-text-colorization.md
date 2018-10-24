---
title: 取得字型和色彩資訊文字的顏色標示 |Microsoft Docs
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
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 49a787dd67691c581383713a7c98a80816762599
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832715"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>取得字型和色彩資訊文字的顏色標示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

呈現，或在使用者介面 (UI) 項目中顯示彩色的文字的程序取決於專案、 技術和開發人員的喜好設定的類型。 **字型和色彩**屬性頁會將設定儲存。  
  
 需要顯示彩色的文字的大部分實作`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults`和相關聯的呈現、 擷取和儲存文字顯示設定的介面。  
  
> [!NOTE]
>  當自訂核心編輯器 (支援**文字 EditorCategory**)，強烈建議您在語言服務中使用著色技術。 如需詳細資訊，請參閱 <<c0> [ 字型和色彩概觀](../extensibility/font-and-color-overview.md)。  
  
## <a name="getting-default-font-and-color-information"></a>取得預設字型和色彩資訊  
 所有**字型和色彩**應指定設定的任何視窗，以顯示文字**顯示項目**之一**分類**。 如需詳細資訊，請參閱 <<c0> [ 字型和色彩、 環境、 選項對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
 若要以色彩標示，VSPackage 必須取得目前**字型和色彩**設定。 VSPackage 可以完成這項作業以下列方式，根據其需求：  
  
- 您可以使用的字型和色彩的持續性機制來擷取預存] 或 [目前狀態。 如需詳細資訊，請參閱 <<c0> [ 存取儲存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
- 使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面的服務，提供要取得的執行個體的字型和色彩資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>，如果 VSPackage 也不是字型和色彩提供者。  
  
- 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 介面。  
  
  若要確保透過輪詢所得到的結果是最新狀態，可能會使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，以判斷更新是否需要在呼叫的擷取方法之前<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。  
  
  取得字型和色彩資訊之後，剖析來識別需要顏色標示的項目要顯示的文字，然後使用適當的字型和色彩 視窗中顯示文字。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [使用字型和文字](http://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [使用色彩](http://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI （繪圖裝置介面）](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)

