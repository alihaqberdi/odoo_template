odoo
=

Required Software
-

1. Install Python 3.10 or higher
2. Install postgresql 13 or higher

Setup Instructions
-

1. Clone the repository

```bash
git clone --depth 1 https://github.com/odoo/odoo.git
```

2. Create a new postgres user with username: `odoo` and password: `odoo`

```sql
sudo -u postgres createuser -s odoo_user
sudo -u postgres psql
ALTER USER odoo_user WITH password 'odoo';
```

3. Create a new virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
```

4. As some of the Python packages need a compilation step, they require system libraries to be installed. You should
   install these required libraries:

```bash
sudo apt install python3-pip libldap2-dev libpq-dev libsasl2-dev
```

5. Install the requirements. Before installing the requirements, you should remove all `psycopg2` packages from the
   requirements.txt file and add `psycopg2-binary==2.9.9` package. Then install the requirements.

```bash
pip install -r odoo/requirements.txt
```

5. Install wkhtmltopdf

```bash
sudo apt update
sudo apt -y install wkhtmltopdf
```

6. Run the server with the following command:

```bash
python odoo/odoo-bin -c conf/odoo.conf -d odoo
```

The server will be running on `localhost:8069`

