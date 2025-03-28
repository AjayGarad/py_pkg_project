# This project define how to create pypi package

- In this project we have created package with name `pkg_test_random`.
- link to package: `https://pypi.org/project/pkg-test-random/0.1.0/`
- Note that before giving the name to packge please check whether package name is available or not to upload - `https://pypi.org/help/#project-name-claim`

1. Install Required Tools
    - Make sure you have twine and build installed:

    ```bash
    pip install -f twine build
    ```

2. Build Your Package
    - Navigate to your project folder and run:

    ```bash
    python -m build
    ```

3. Create a PyPI Account
    - Go to PyPI and sign up.

    1. Enable 2FA on PyPI
        - Go to PyPI Account Settings.
        - Under "Two-factor Authentication", enable TOTP (Time-based One-Time Passwords).
        - Scan the QR code with an authenticator app (like Google Authenticator or Authy).
        - Enter the generated 6-digit code to confirm.

    2. Generate an API Token
        - After enabling 2FA, go back to Account Settings.
        - Scroll down to "API tokens" and click "Add API Token".
        - Give it a name (e.g., mypackage-publish).
        - Copy the generated token immediately, as it won’t be shown again.

4. Upload the Package
    1. Run the following command and enter your credentials when prompted:

        ```bash
        twine upload dist/*
        ```

    2. If using an API token, run:

        ```bash
        twine upload dist/* -u __token__ -p YOUR_API_TOKEN
        ```

    3. For security, you can store the token in `~/.pypirc`:

        ```bash
        [distutils]
            index-servers =
                pypi

        [pypi]
            username = __token__
            password = YOUR_API_TOKEN
        ```

    - Once you've stored the API token in `~/.pypirc`, you can upload your package without manually entering credentials by running:

        ```bash
        twine upload dist/*
        ```

    - Since twine automatically reads the credentials from `~/.pypirc`, it will use the stored API token without requiring manual input.
