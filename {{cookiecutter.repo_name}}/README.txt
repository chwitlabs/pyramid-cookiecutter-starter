{{ cookiecutter.project_name }}
{% for _ in cookiecutter.project_name %}={% endfor %}

Getting Started
---------------

- Install poetry.
    curl -sSL https://raw.githubusercontent.com/sdispater/poetry/master/get-poetry.py | python

- Change directory into your newly created project.

    cd {{ cookiecutter.repo_name }}

- Install the project in editable mode with its development dependencies.

    poetry install

{% if cookiecutter.backend == 'sqlalchemy' -%}
- Initialize and upgrade the database using Alembic.

    - Generate your first revision.

        poetry run alembic -c development.ini revision --autogenerate -m "init"

    - Upgrade to that revision.

        poetry run alembic -c development.ini upgrade head

- Load default data into the database using a script.

    poetry run initialize_{{ cookiecutter.repo_name }}_db development.ini

{% endif -%}
- Run your project's tests.

    poetry run pytest

- Run your project.

    poetry run pserve development.ini
