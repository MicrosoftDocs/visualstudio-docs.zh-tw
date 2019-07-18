---
title: VSCT XML 結構描述條件式屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422145"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 結構描述條件式屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

條件式屬性可以套用至所有清單和項目。 邏輯運算子和符號展開的運算式評估為 true 或 false。 如果為 true，也是產生的輸出中包含相關聯的清單或項目。  
  
 針對其他語彙基元展開或常數，您可以測試權杖的擴充。 Defined() 函式用來測試是否已定義特定的名稱，即使它沒有任何值。  
  
 當條件屬性套用至清單時，條件會套用至清單中每個子元素。 如果子系項目本身包含條件屬性，然後其條件結合的父代運算式 AND 作業。  
  
 值 1，'1' 和 'true' 會評估為 true，和 0、 '0' 和 'false' 評估為 false。  
  
## <a name="operators"></a>運算子  
 下列運算子可能會用來評估條件運算式中。  
  
|運算子|定義|  
|--------------|----------------|  
|(,)|群組|  
|!|邏輯 NOT|  
|\<, >, \<=, >=, ==, !=|關係與相等|  
|和|Boolean|  
|或|Boolean|  
  
## <a name="examples"></a>範例  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
