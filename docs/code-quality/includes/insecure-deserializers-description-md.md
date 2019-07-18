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
還原序列化未受信任的資料時，不安全的反序列化程式是易受攻擊。 攻擊者可以修改要包含未預期的型別，以將物件插入具有惡意的副作用的序列化的資料。 攻擊不安全的還原序列化程式可以比方說，在基礎作業系統上執行命令、 透過網路通訊或刪除檔案。