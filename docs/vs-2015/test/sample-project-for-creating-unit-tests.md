---
title: 用於建立單元測試的範例專案 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d495d0bf12c900d34a04a84e950b002494b7b5c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660402"
---
# <a name="sample-project-for-creating-unit-tests"></a>用於建立單元測試的範例專案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

所提供的這個範例程式碼可用於下列逐步解說：

- [逐步解說：針對 Managed 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)。 此逐步解說會引導您逐步完成建立及自訂單元測試、加以執行，以及檢查測試結果。

- [逐步解說：執行測試並檢視程式碼涵蓋範圍](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)。 此逐步解說將說明如何檢視程式碼涵蓋範圍資料，該資料會顯示專案程式碼中正在受測試的部分。

- [逐步解說：使用命令列測試公用程式](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)。 在此逐步解說中，您可以使用 MSTest.exe 命令列公用程式來執行測試及檢視結果。

## <a name="sample-code"></a>程式碼範例
 此範例中唯一刻意設計的錯誤是在 Debit 方法 "m_balance += amount" 中，等號前面應該是減號，而不是加號。

```
using System;

namespace BankAccountNS
{
    /// <summary>
    /// Bank Account demo class.
    /// </summary>
    public class BankAccount
    {
        private string m_customerName;

        private double m_balance;

        private bool m_frozen = false;

        private BankAccount()
        {
        }

        public BankAccount(string customerName, double balance)
        {
            m_customerName = customerName;
            m_balance = balance;
        }

        public string CustomerName
        {
            get { return m_customerName; }
        }

        public double Balance
        {
            get { return m_balance; }
        }

        public void Debit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount > m_balance)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount; // intentionally incorrect code
        }

        public void Credit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount;
        }

        private void FreezeAccount()
        {
            m_frozen = true;
        }

        private void UnfreezeAccount()
        {
            m_frozen = false;
        }

        public static void Main()
        {
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

            ba.Credit(5.77);
            ba.Debit(11.22);
            Console.WriteLine("Current balance is ${0}", ba.Balance);
        }

    }
}
```

 /* 此處所描述的範例公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點與事件均屬虛構。  並非影射任何真實的公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點或事件。 \*/

## <a name="working-with-the-code"></a>使用程式碼
 若要使用此程式碼，您必須先在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中為其建立專案。 請遵循[逐步解說：針對 Managed 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)中＜準備逐步解說＞一節的步驟。

## <a name="see-also"></a>請參閱
 [逐步解說：建立和執行 Managed 程式碼的單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)[逐步解說：執行測試和觀看程式碼涵蓋範圍](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)[逐步解說：使用命令列測試公用程式](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)
