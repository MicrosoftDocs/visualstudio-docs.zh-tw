---
title: BeginCapture |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0c04f199472afc516304f7a8f4f135174593b60
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473611"
---
# <a name="begincapture"></a>BeginCapture
開始將結尾擷取間隔`EndCapture`。  
  
## <a name="syntax"></a>語法  
  
```C++  
void BeginCapture();  
```  
  
## <a name="remarks"></a>備註  
 在擷取間隔通常會跨越一個畫面，例如當您想要擷取的相關特定種類的繪製呼叫的圖形資訊的子集。 如果擷取間隔跨越呈現的呼叫，會擷取這兩個框架的圖形資訊。 第一個框架橫跨的呼叫之間的間隔`BeginCapture`和呈現; 呼叫第二個框架橫跨呈現呼叫之後的第一個 Direct3D 事件和呼叫之間的間隔`EndCapture`。  
  
 若要擷取的間隔，您必須準備您的應用程式來擷取和記錄的圖形資訊 — 也就是您必須先呼叫[Init](init.md)的執行個體透過`VsgDbg`類別才能呼叫`BeginCapture`或`EndCapture`。  
  
## <a name="see-also"></a>另請參閱  
 [EndCapture](endcapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)