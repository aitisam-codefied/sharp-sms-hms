## 🍽️ Food Module

Manages meals, categories, and guest feedback regarding food services.

---

### 📌 Routes

`/api/v1/food`

#### 🥘 Food

| Method | Endpoint | Description    |
| ------ | -------- | -------------- |
| GET    | `/`      | List all meals |
| POST   | `/`      | Create a meal  |
| GET    | `/:id`   | Get meal by ID |
| PATCH  | `/:id`   | Update a meal  |
| DELETE | `/:id`   | Delete a meal  |

#### 🗂️ Category

| Method | Endpoint                | Description          |
| ------ | ----------------------- | -------------------- |
| POST   | `/category`             | Create food category |
| GET    | `/category/:categoryId` | Meals by category    |
| PATCH  | `/category/:id`         | Update category      |
| DELETE | `/category/:id`         | Delete category      |

#### 🗣️ Feedback

| Method | Endpoint                | Description             |
| ------ | ----------------------- | ----------------------- |
| POST   | `/:foodId/feedback`     | Submit feedback         |
| GET    | `/:foodId/feedback`     | Get feedback for a meal |
| PATCH  | `/feedback/:feedbackId` | Update feedback         |
| DELETE | `/feedback/:feedbackId` | Delete feedback         |

---

### 🔐 Protected by

* `authGuard`
* `checkPermission('food' | 'foodCategory' | 'foodFeedback', action)`

---

### 🧠 Use Cases

* Manage daily or weekly menus per branch
* Categorize meals: Breakfast, Dinner, Special
* Guests provide feedback tied to specific meals
* Admins track satisfaction metrics

---

### 📦 Key Fields

* `name`, `description`, `price`
* `categoryId`, `branchId`
* `feedback.rating`, `feedback.comment`, `guestId`

---

> The food module is useful for nutrition tracking, menu planning, and capturing direct guest experience.