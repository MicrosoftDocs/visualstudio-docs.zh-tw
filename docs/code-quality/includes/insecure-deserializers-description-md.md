---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "89325512"
---
在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 針對不安全的還原序列化程式進行攻擊，例如，在基礎作業系統上執行命令、透過網路進行通訊，或刪除檔案。