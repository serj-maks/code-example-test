```java
// source: ilya-java-mentoring-streams-5
public static List<String> amountMoneyBelowMin(int min, List<Client> clients) {
    return clients.stream()
            .map(client -> client.getAccounts())
            .flatMap(account -> account.stream())
            .filter(account -> account.getAmountMoney() > min)
            .map(account -> account.getAccountNumber())
            .collect(Collectors.toList());
}
```
