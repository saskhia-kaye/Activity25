# Activity25
SOLID PRINCIPLES in Angular

SOLID Principles:

SOLID principles, their importance, and how they improve code quality, maintainability, and scalability in Angular applications.

S - Single Responsibility Principle (SRP):

Explanation: Each component, service, or module should only have one responsibility.

Angular Example: Create a separate service for handling API calls rather than embedding HTTP requests within a component. This way, components focus on managing the UI, while services manage the data.

export abstract class NotificationService {
  abstract send(message: string): void;
}

@Injectable()
export class EmailNotificationService extends NotificationService {
  send(message: string) {
    console.log('Email sent:', message);
  }
}

@Injectable()
export class SmsNotificationService extends NotificationService {
  send(message: string) {
    console.log('SMS sent:', message);
  }
}


Real-world Use Case: Separating responsibilities keeps your code easier to test and debug.

Open/Closed Principle (OCP):

Explanation: Classes should be open for extension but closed for modification.

Angular Example: Use inheritance or dependency injection for adding new behaviors without changing existing code.

export abstract class NotificationService {
  abstract send(message: string): void;
}

@Injectable()
export class EmailNotificationService extends NotificationService {
  send(message: string) {
    console.log('Email sent:', message);
  }
}

@Injectable()
export class SmsNotificationService extends NotificationService {
  send(message: string) {
    console.log('SMS sent:', message);
  }
}


Real-world Use Case: Easily add new notification types by extending NotificationService without modifying existing classes.

Liskov Substitution Principle (LSP):

Explanation: Subtypes must be substitutable for their base types without altering the correctness of the program.

Angular Example: Ensure that extended classes can replace the base class without introducing errors.

class BasicUser {
  accessLevel = 'basic';
  login() { /*...*/ }
}

class AdminUser extends BasicUser {
  accessLevel = 'admin';
  deleteContent() { /*...*/ }
}


Real-world Use Case: AdminUser should be able to perform all actions of a BasicUser without breaking functionality.

Interface Segregation Principle (ISP):

Explanation: Clients should not be forced to depend on interfaces they do not use.

Angular Example: Split large interfaces into smaller, specific ones.

interface CanRead {
  read(): void;
}
interface CanWrite {
  write(): void;
}
class Editor implements CanRead, CanWrite {
  read() { /*...*/ }
  write() { /*...*/ }
}


Real-world Use Case: A user interface with specific roles avoids implementing unnecessary methods.

Dependency Inversion Principle (DIP):

Explanation: High-level modules should not depend on low-level modules; both should depend on abstractions.

Angular Example: Use Angular's Dependency Injection to inject services based on interfaces, which promotes testability and flexibility.

@Injectable()
export class UserComponent {
  constructor(private notificationService: NotificationService) {}
  notifyUser(message: string) {
    this.notificationService.send(message);
  }
}


Real-world Use Case: You can replace NotificationService with any other implementation as long as it follows the NotificationService interface.
