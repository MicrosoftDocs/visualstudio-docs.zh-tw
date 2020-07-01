---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147079"
---
還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。 例如，對不安全的還原序列化程式的攻擊可能會在基礎作業系統上執行命令、透過網路進行通訊，或刪除檔案。