# Contribuir a **Nombre del proyecto**

Por favor tómate un momento para revisar éste documento ya que ayuda a entender el 
proceso de contribuir además de hacerlo simple y efectivo para todos los involucrados.

También es importante que leas el [Código de conducta](LINK AL DOCUMENTO) que define
nuestro compromio hacia un ambiente abierto y que da la bienvenida a todos los involucrados.

## Registro de problemas _Issue tracker_

Utiliza el registros de problemas para:

* [Reporte de errores](#bug-reports)
* [Enviar _pull requests_](#pull-requests)

Por favor **no uses* el registros de problemas como una manera de obtener soporte personal, ni como herramienta para solicitar nuevas características.
Solicitudes de reporte deben de ser enviadas a:

* [Lista de correos](LINK A LA LISTA)
* [Stack Overflow](http://stackoverflow.com/questions/ask?tags=ETIQUETA)

Para solicitar nuevas características la solicitud se puede hacer en [Lista de discusión](LINK_A_LA_LIST).

Hacemos los mejor posible para mantener la lista de errores pequeña y organizada, de manera
que sea útil para todos. Por ejemplo, clasificamos los errores en base a la dificultad percivida,
para que sea más sencillo a otros desarrolladores el [contribuir al proyecto](#contributing).

## Reporte de errores

Un error es un _problema demostrable_ que es causado por el código en el repositorio.
Buenos reportes de errores son extremadamente útiles - Gracias!

Guía para el reporte de errores:

1. **Utiliza la busqueda de GitHub** &mdash; [Para revisaer que el error no ha sido reportado con anterioridad](https://github.com/USUARIO/PROYECTO/search?type=Issues).

2. **Verifique si el error ha sido corregido** &mdash; trate de reproducirlo utilizando el _branch_ de `master` en el repositorio.

3. **Aisle y reporte el problema** &mdash; idealmente creado para reducir el caso a probar.

Por favor trate de ser lo más detallado posible en su reporte. Incluya información acerca de
su sistema operativo y la versión de librerías importantes. Describa los pasos para reproducir 
el problema y cuál es el resultado esperado. Todos estos detalles ayudan a los desarrolladores 
a resolver cualquier error potencial.

Ejemplo:

> Título del problema corto y descriptivo
>
> Un resumen del problema y del ambiente en él que ocurre. Si es posible, 
> incluya los pasos necesarios para reproducirlo.
>
> 1. Primer paso
> 2. Segundo paso
> 3. Pasos adicionales
>
> `<url>` - un link con código para reproducir el problema (ej. a GitHub Gist)
>
> Cualquiér otra información que quieras compartir y que sea relevante para el problema
> descrito. Esto puede incluir las líneas de código que tu haz identificado como el causante
> del error y sus soluciones potenciales (y tú opinión de los méritos de la solución).

## Solicitud de nuevas características

 Feature requests are welcome and should be discussed on [the elixir-core mailing list](https://groups.google.com/group/elixir-lang-core). But take a moment to find
out whether your idea fits with the scope and aims of the project. It's up to *you*
to make a strong case to convince the community of the merits of this feature.
Please provide as much detail and context as possible.

## Contributing

We incentivize everyone to contribute to Elixir and help us tackle
existing issues! To do so, there are a few things you need to know
about the code. First, Elixir code is divided in applications inside
the `lib` folder:

* `elixir` - Contains Elixir's kernel and stdlib

* `eex` - Template engine that allows you to embed Elixir

* `ex_unit` - Simple test framework that ships with Elixir

* `iex` - IEx, Elixir's interactive shell

* `mix` - Elixir's build tool

You can run all tests in the root directory with `make test` and you can
also run tests for a specific framework `make test_#{NAME}`, for example,
`make test_ex_unit`.

In case you are changing a single file, you can compile and run tests only
for that particular file for fast development cycles. For example, if you
are changing the String module, you can compile it and run its tests as:

```sh
bin/elixirc lib/elixir/lib/string.ex -o lib/elixir/ebin
bin/elixir lib/elixir/test/elixir/string_test.exs
```

After your changes are done, please remember to run the full suite with
`make test`.

From time to time, your tests may fail in an existing Elixir checkout and
may require a clean start by running `make clean compile`. You can always
check [the official build status on Travis-CI](https://travis-ci.org/elixir-lang/elixir).

With tests running and passing, you are ready to contribute to Elixir and
send your pull requests.

## Contributing Documentation

Code documentation (`@doc`, `@moduledoc`, `@typedoc`) has a special convention:
the first paragraph is considered to be a short summary.

For functions, macros and callbacks say what it will do. For example write
something like:

```elixir
@doc """
Returns only those elements for which `fun` is `true`.

...
"""
def filter(collection, fun) ...
```

For modules, protocols and types say what it is. For example write
something like:

```elixir
defmodule File.Stat do
  @moduledoc """
  Information about a file.

  ...
  """

  defstruct [...]
end
```

Keep in mind that the first paragraph might show up in a summary somewhere, long
texts in the first paragraph create very ugly summaries. As a rule of thumb
anything longer than 80 characters is too long.

Try to keep unnecessary details out of the first paragraph, it's only there to
give a user a quick idea of what the documented "thing" does/is. The rest of the
documentation string can contain the details, for example when a value and when
`nil` is returned.

If possible include examples, preferably in a form that works with doctests. For
example:

```elixir
@doc """
Returns only those elements for which `fun` is `true`.

## Examples

    iex> Enum.filter([1, 2, 3], fn(x) -> rem(x, 2) == 0 end)
    [2]

"""
def filter(collection, fun) ...
```

This makes it easy to test the examples so that they don't go stale and examples
are often a great help in explaining what a function does.

## Pull requests

Good pull requests - patches, improvements, new features - are a fantastic
help. They should remain focused in scope and avoid containing unrelated
commits.

**NOTE**: Do not send code style changes as pull requests like changing
the indentation of some particular code snippet or how a function is called.
Those will not be accepted as they pollute the repository history with non
functional changes and are often based on personal preferences.

**IMPORTANT**: By submitting a patch, you agree that your work will be
licensed under the license used by the project.

If you have any large pull request in mind (e.g. implementing features,
refactoring code, etc), **please ask first** otherwise you risk spending
a lot of time working on something that the project's developers might
not want to merge into the project.

Please adhere to the coding conventions in the project (indentation,
accurate comments, etc.) and don't forget to add your own tests and
documentation. When working with Git, we recommend the following process
in order to craft an excellent pull request:

1. [Fork](https://help.github.com/fork-a-repo/) the project, clone your fork,
  and configure the remotes:

  ```sh
  # Clone your fork of the repo into the current directory
  git clone https://github.com/<your-username>/elixir
  # Navigate to the newly cloned directory
  cd elixir
  # Assign the original repo to a remote called "upstream"
  git remote add upstream https://github.com/elixir-lang/elixir
  ```

2. If you cloned a while ago, get the latest changes from upstream:

  ```sh
  git checkout master
  git pull upstream master
  ```

3. Create a new topic branch (off of `master`) to contain your feature, change,
  or fix.

  **IMPORTANT**: Making changes in `master` is discouraged. You should always
  keep your local `master` in sync with upstream `master` and make your
  changes in topic branches.

  ```sh
  git checkout -b <topic-branch-name>
  ```

4. Commit your changes in logical chunks. Keep your commit messages organized,
  with a short description in the first line and more detailed information on
  the following lines. Feel free to use Git's
  [interactive rebase](https://help.github.com/articles/interactive-rebase)
  feature to tidy up your commits before making them public.

5. Make sure all the tests are still passing.

  ```sh
  make test
  ```

  This command will compile the code in your branch and use that
  version of Elixir to run the tests. This is needed to ensure your changes can
  pass all the tests.

6. Push your topic branch up to your fork:

  ```sh
  git push origin <topic-branch-name>
  ```

7. [Open a Pull Request](https://help.github.com/articles/using-pull-requests/)
  with a clear title and description.

8. If you haven't updated your pull request for a while, you should consider
  rebasing on master and resolving any conflicts.

  **IMPORTANT**: _Never ever_ merge upstream `master` into your branches. You
  should always `git rebase` on `master` to bring your changes up to date when
  necessary.

  ```sh
  git checkout master
  git pull upstream master
  git checkout <your-topic-branch>
  git rebase master
  ```

We have saved some excellent pull requests we have received in the past in case
you are looking for some examples:

* [Implement Enum.member? – Pull Request](https://github.com/elixir-lang/elixir/pull/992)
* [Add String.valid? – Pull Request](https://github.com/elixir-lang/elixir/pull/1058)
* [Implement capture_io for ExUnit – Pull Request](https://github.com/elixir-lang/elixir/pull/1059)

Thank you for your contributions!
