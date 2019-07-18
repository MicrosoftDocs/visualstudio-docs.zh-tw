---
title: 存取遭到拒絕 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9563cafa4895f89253b4073d788240806a86fa2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561074"
---
# <a name="access-is-denied"></a>存取遭拒。
指令碼嘗試從來源而不是目前頁面的主機存取資料。 Internet Explorer 及其他瀏覽器所遵循的相同來源原則，只允許程式碼從具有相同配置、主機和目前頁面之 URL 連接埠的來源存取資料。  
  
 例如，如果目前的頁面是`https://employees.mycompany.com`，您無法從下列 Url 來存取資料：  
  
- `http://data.contoso.com`因為它正在使用 HTTP 而不 HTTPS。  
  
- `https://somedatasource.com`因為它是不同的網域。  
  
- `https://employees.mycompany.com:8888`因為它會使用不同的連接埠。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 調查您要呼叫的 API，是否支援 JSONP 或 CORS (這兩種方法允許跨原始指令碼處理，而且安全無虞)。  
  
- 如果您要嘗試呼叫 REST API，請將此呼叫重構為您的伺服器端程式碼，然後向您的用戶端指令碼公開新的 REST 端點。  
  
     如需其他資訊，請尋找相同來源原則、JSONP 及 CORS 的相關線上文件。
