---
title: 用於建立單元測試的範例程式碼
description: 本文提供可在 Visual Studio 中使用單元測試進行測試的範例程式碼。
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93a6627b96daefa48c9a72fd84726775fc449bde
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="sample-code-for-testing"></a>用於測試的範例程式碼

此範例程式碼包含類別 *BankAccount*，其中包含可透過單元測試進行測試的各種方法。

下列逐步解說中會使用此程式碼：

- [針對受控碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). 此逐步解說會引導您逐步完成建立及自訂單元測試、加以執行，以及檢查測試結果。
- [使用命令列測試公用程式](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)。 在此逐步解說中，您可以使用 MSTest.exe 命令列公用程式來執行測試及檢視結果。

## <a name="sample-code"></a>範例程式碼

此範例中唯一刻意設計的錯誤是在 Debit 方法 "m_balance += amount" 中，等號前面應該是減號，而不是加號。

```csharp
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

/* 此處所描述的範例公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點與事件均屬虛構。 並非影射任何真實的公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點或事件。 \*/

## <a name="create-the-project"></a>建立專案

若要使用此程式碼，請先在 Visual Studio 中為它建立專案。 遵循[逐步解說：針對受控碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test)中的步驟以建立專案。

## <a name="see-also"></a>另請參閱

- [逐步解說：針對受控碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [逐步解說：使用命令列測試公用程式](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
