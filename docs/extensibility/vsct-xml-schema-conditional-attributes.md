---
title: VSCT XML 結構描述條件式屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b31b99e38eeec2ff1e5e31bc6bdaeed3d3be3d83
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586817"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 結構描述條件式屬性
您可以將條件式屬性套用至所有清單和項目。 邏輯運算子和符號展開的運算式評估為 true 或 false。 如果為 true，也是產生的輸出中包含相關聯的清單或項目。  
  
 您可以測試對其他語彙基元展開或常數的語彙基元展開。 此函式`Defined()`測試是否已定義特定的名稱，即使它沒有任何值。  
  
 當條件屬性套用至清單時，條件會套用至清單中每個子元素。 如果子系項目本身包含條件屬性，然後其條件結合的父代運算式 AND 作業。  
  
 值 1，'1' 和 'true' 會評估為 true，和 0、 '0' 和 'false' 評估為 false。  
  
## <a name="operators"></a>運算子  
 您可以使用下列運算子來評估條件運算式。  
  
|運算子|定義|  
|--------------|----------------|  
|(,)|群組|  
|!|邏輯 NOT|  
|\<, >, \<=, >=, ==, !=|關係與相等|  
|和|Boolean|  
|或|Boolean|  
  
## <a name="examples"></a>範例  
  
```xml  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)