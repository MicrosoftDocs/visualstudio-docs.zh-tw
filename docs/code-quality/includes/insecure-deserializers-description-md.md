---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 43327901b2233b9b2818296f9269975d8524438b
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367266"
---
還原序列化未受信任的資料時，不安全的反序列化程式是易受攻擊。 攻擊者可以修改要包含未預期的類型，具有惡意的副作用的序列化的資料。 攻擊不安全的還原序列化程式可以比方說，在基礎作業系統上執行命令、 透過網路通訊或刪除檔案。