# React Router Notes

## Introduction
React Router is a standard routing library for React applications. It enables the navigation among views in a React application, allowing for a single-page app experience.

## Key Concepts

### 1. BrowserRouter
- Wraps your application and creates a history object.
- Uses HTML5 history API to keep UI in sync with URL.

```jsx
import { BrowserRouter } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      {/* Your app components */}
    </BrowserRouter>
  );
}
```

### 2. Route
- Renders some UI when its path matches the current URL.

```jsx
import { Route } from 'react-router-dom';

<Route path="/about" element={<About />} />
```

### 3. Routes
- Renders the first child `<Route>` that matches the location.

```jsx
import { Routes, Route } from 'react-router-dom';

<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
  <Route path="/contact" element={<Contact />} />
</Routes>
```

### 4. Link
- Creates an anchor tag for linking to routes.

```jsx
import { Link } from 'react-router-dom';

<Link to="/about">About</Link>
```

### 5. NavLink
- A special kind of `<Link>` that can style itself as "active" when its `to` prop matches the current location.

```jsx
import { NavLink } from 'react-router-dom';

<NavLink to="/about" className={({ isActive }) => isActive ? 'active' : ''}>
  About
</NavLink>
```

### 6. Navigate
- For programmatic navigation.

```jsx
import { Navigate } from 'react-router-dom';

function PrivateRoute({ authenticated }) {
  return authenticated ? <PrivateComponent /> : <Navigate to="/login" />;
}
```

### 7. Outlet
- Used for nested routes, renders child routes.

```jsx
import { Outlet } from 'react-router-dom';

function Dashboard() {
  return (
    <div>
      <h1>Dashboard</h1>
      <Outlet /> {/* Child routes render here */}
    </div>
  );
}
```

### 8. useParams
- Hook to access URL parameters.

```jsx
import { useParams } from 'react-router-dom';

function UserProfile() {
  let { id } = useParams();
  return <div>User ID: {id}</div>;
}
```

### 9. useNavigate
- Hook for programmatic navigation.

```jsx
import { useNavigate } from 'react-router-dom';

function SignUpForm() {
  let navigate = useNavigate();
  
  function handleSubmit(event) {
    event.preventDefault();
    // ... handle form submission
    navigate('/dashboard');
  }

  return (/* form JSX */);
}
```

## Best Practices
1. Keep your routes organized in a central location.
2. Use dynamic routes for reusable components.
3. Implement proper error handling and 404 routes.
4. Use lazy loading for better performance in larger apps.
5. Protect routes that require authentication.

## Conclusion
React Router provides a powerful and flexible way to handle routing in React applications. By understanding and effectively using its components and hooks, you can create intuitive and efficient navigation systems for your users.
