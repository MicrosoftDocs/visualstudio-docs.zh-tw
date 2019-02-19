---
title: 類別檢視和物件瀏覽器圖示 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cb80c7ad81708724750660560d65cfef722af86
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785045"
---
# <a name="class-view-and-object-browser-icons"></a>類別檢視和物件瀏覽器圖示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[類別檢視]** 和 [物件瀏覽器] 會顯示代表程式碼實體 (例如，命名空間、類別、函式和變數) 的圖示。 下表說明並描述圖示。  
  
|圖示|描述|圖示|描述|  
|----------|-----------------|----------|-----------------|  
|![命名空間符號](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|命名空間|![宣告符號](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|方法或函式|  
|![類別圖示](../ide/media/vxclass-icon.gif "vxClass_Icon")|類別|![運算子符號](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|運算子|  
|![介面棒棒糖符號](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|介面|![屬性符號](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|屬性|  
|![結構符號](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|結構|![欄位圖示](../ide/media/vxfield-icon.gif "vxField_Icon")|欄位或變數|  
|![聯集符號](../ide/media/vxunion-icon.gif "vxUnion_Icon")|聯集|![事件符號](../ide/media/vxevent-icon.gif "vxEvent_Icon")|Event - 事件|  
|![列舉符號](../ide/media/vxenum-icon.gif "vxEnum_Icon")|列舉|![常數圖示](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|常數|  
|![類型定義符號](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|Typedef|![列舉項目符號](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|列舉項目|  
|![Visual Studio 模組符號](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Module|![對應項目符號](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|對應項目|  
|![擴充方法符號](../ide/media/extensionmethod.gif "ExtensionMethod")|擴充方法|![宣告符號](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|外部宣告|  
|![委派符號](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|Delegate - 委派|![[類別檢視] 和 [物件瀏覽器] 的錯誤圖示](../ide/media/erroricon.gif "ErrorIcon")|錯誤|  
|![例外狀況符號](../ide/media/vxexception-icon.gif "vxException_Icon")|例外|![範本符號](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|範本|  
|![對應符號](../ide/media/vxmap-icon.gif "vxMap_Icon")|對應|![錯誤驚嘆號符號](../ide/media/vxerror-icon.gif "vxError_Icon")|不明|  
|![類型轉送符號](../ide/media/ob-type-forward.gif "ob_type_forward")|類型轉送|||  
  
## <a name="signal-icons"></a>信號圖示  
 下列訊號圖示套用至所有先前的圖示，並指出其存取範圍。  
  
> [!NOTE]
>  如果您的專案包含在原始檔控制資料庫中，則可能會顯示其他訊號圖示以指出原始檔控制狀態 (例如存回或取出)。  
  
|圖示|描述|  
|----------|-----------------|  
|\<無訊號圖示>|公用。 可從此元件中的任何位置以及任何參考它的元件存取。|  
|![訊號保護符號](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|受保護。 可從包含類別或類型存取，或從衍生自包含類別或類型的包含類別或類型存取。|  
|![訊號私用符號](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Key")|私用。 只能在包含類別或類型中存取。|  
|![訊號密封符號](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Key")|密封。|  
|![訊號 Friend&#47;內部符號](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Friend/內部。 只能從專案存取。|  
|![訊號圖示箭號](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|捷徑。 物件的捷徑。|  
  
## <a name="see-also"></a>請參閱  
 [檢視程式碼的結構](../ide/viewing-the-structure-of-code.md)
