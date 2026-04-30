```mermaid
classDiagram
    class BankUI {
        +displayMenu() void
        +inputUserData() void
        +requestTransaction() void
    }

    class User {
        -id: String
        -pw: String
        -name: String
        -phone: String
        -address: String
        +registerUser(id: String, pw: String, name: String, phone: String, address: String) void
        +updateUser(id: String, pw: String, name: String, phone: String, address: String) void
        +deleteUser(id: String) void
        +searchUser(id: String) User
    }

    class Account {
        -number: String
        -balance: long
        +deposit(userId: String, amount: long) void
        +withdraw(userId: String, amount: long) boolean
        +transfer(userId: String, targetNumber: String, amount: long) boolean
        +computeBalance() long
    }

    %% 관계 설정
    %% BankUI는 Account에 의존함
    BankUI ..> Account : 사용

    %% User 1명당 Account 1개 이상 (연관 관계)
    User "1" <-- "1..*" Account : 사용자 조회(Association)