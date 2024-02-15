# wirewire code
class BankAccount:
    def __init__(self, account_number, balance=0):
        self.account_number = account_number
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount
        print(f"Deposited ${amount}. New balance: ${self.balance}")

    def withdraw(self, amount):
        if self.balance >= amount:
            self.balance -= amount
            print(f"Withdrew ${amount}. New balance: ${self.balance}")
        else:
            print("Insufficient funds")

class WireTransfer:
    @staticmethod
    def transfer(sender_account, recipient_account, amount):
        if sender_account.balance >= amount:
            sender_account.withdraw(amount)
            recipient_account.deposit(amount)
            print(f"Wire transfer of ${amount} from account {sender_account.account_number} to {recipient_account.account_number} completed successfully")
        else:
            print("Wire transfer failed: Insufficient funds in sender's account")

# Example usage
if __name__ == "__main__":
    sender_account = BankAccount(account_number="123456", balance=1000)
    recipient_account = BankAccount(account_number="789012", balance=500)

    print("Sender's account balance:", sender_account.balance)
    print("Recipient's account balance:", recipient_account.balance)

    WireTransfer.transfer(sender_account, recipient_account, 300)

    print("Sender's account balance after transfer:",
