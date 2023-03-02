# Askas API Documentation

## Endpoints

### Authorization

- `/auth/sign_in/`</br>
    - **request**:
        - body: 
            ```json
            {
                email: string,
                password: string
            }
            ```
    - **response**:
        - 200 OK:
            ```json
            {
                accessToken: string,
                refreshToken: string,
            }
            ```
        - 400 BadRequest:
            - Request must contain both fields
                ```json
                {
                    error: "email is not specified"
                }
                ```
                or
                ```json
                {
                    error: "password is not specified"
                }
                ```
            - Email must be unique
                ```json
                {
                    error: "user with specified email already exists"
                }
                ```
            - Email must be valid
                ```json
                {
                    error: "specified email is not valid"
                }
                ```
            - Password must be valid
                ```json
                {
                    error: "password must be at least 8 characters long"
                }
                ```
                or
                 ```json
                {
                    error: "password must contain both lowercase and uppercase characters"
                }
                ```
                or
                ```json
                {
                    error: "password must contain digits 0-9"
                }
                ```
                or
                ```json
                {
                    error: "password must contain special characters '!@#$%&*'"
                }
                ```
        - 403 Forbidden:
            ```json
            {
                error: "user with this credentials does not exist"
            }
            ```
- `/auth/sign_up/`
- `/auth/refresh/`
