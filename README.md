# Custom VS Code snippets for Frontend Development

JavaScript and React snippets in ES7+ for [VS Code](https://code.visualstudio.com/)

## Installation

Copy the `frontend-snippets` folder to `~/.vscode/extensions` and reload VS Code.

## Supported languages (file extensions)

- JavaScript (.js)
- JavaScript React (.jsx)
- TypeScript (.ts)
- TypeScript React (.tsx)

## Snippets

### React

<details>
  <summary>
    context
  </summary>

  ```tsx
  /**
   * Module dependencies.
   */

  import { Context, createContext, useContext } from 'react';

  /**
   * `Props` type.
   */

  type Props = {
    $2
  };

  /**
   * Export `$1Context` context.
   */

  export const $1Context: Context<Props> = createContext({} as Props);

  /**
   * Export `use$1` hook.
   */

  export const use$1 = () => useContext($1Context);
  ```
</details>

<details>
  <summary>
    provider
  </summary>

  ```tsx
  /**
   * Module dependencies.
   */

  import { $1Context } from './context';
  import React, { ReactNode, useState } from 'react';

  /**
   * `Props` type.
   */

  type Props = {
    children: ReactNode
  };

  /**
   * `$1Provider` provider.
   */

  const $1Provider = ({ children }: Props) => {
    return (
      <$1Context.Provider value={{ $2 }}>
        {children}
      </$1Context.Provider>
    );
  };

  /**
   * Export `$1Provider` provider.
   */

  export default $1Provider;
  ```
</details>

<details>
  <summary>
    rcc | react component
  </summary>

  ```tsx
  /**
   * Module dependencies.
   */

  import { color, media, units } from '@untile/react-components';
  import { ifProp, prop } from 'styled-tools';
  import React, { ReactElement } from 'react';
  import styled, { css } from 'styled-components';

  /**
   * `Props` type.
   */

  type Props = {
    className?: string
  };

  /**
   * `Wrapper` styled component.
   */

  const Wrapper = styled.div`
    position: relative
  `;

  /**
   * `$1` component.
   */

  const $1 = (props: Props): ReactElement => {
    const { className } = props;

    return (
      <Wrapper className={className}>
        $2
      </Wrapper>
    );
  };

  /**
   * Export `$1` component.
   */

  export default $1;
  ```
</details>

<details>
  <summary>
    rcp | react page
  </summary>

  ```tsx
  /**
   * Module dependencies.
   */

  import { color, media, units } from '@untile/react-components';
  import { theme } from 'styled-tools';
  import React, { ReactElement } from 'react';
  import styled from 'styled-components';

  /**
   * `Wrapper` styled page.
   */

  const Wrapper = styled.section`
    position: relative;
  `;

  /**
   * `$1` page.
   */

  const $1 = (): ReactElement => {
    return (
      <>
        <Metatags
          pageTitle={title}
          title={title}
        />

        <Wrapper>
          $2
        </Wrapper>
      </>
    );
  };

  /**
   * Export `$1` page.
   */

  export default $1;
  ```
</details>

<details>
  <summary>
    useCallback
  </summary>

  ```tsx
  useCallback(() => {
    $0
  }, []);
  ```
</details>

<details>
  <summary>
    useEffect
  </summary>

  ```tsx
  useEffect(() => {
    $0
  }, []);
  ```
</details>

<details>
  <summary>
    useMemo
  </summary>

  ```tsx
  useMemo(() => {
    $0
  }, []);
  ```
</details>

<details>
  <summary>
    useState
  </summary>

  ```tsx
  const [$1, set$1] = useState<$2>();
  ```
</details>

### React Query

<details>
  <summary>
    fetch request
  </summary>

  ```ts
  /**
   * Module dependencies.
   */

  import {
    acceptLanguageHeader,
    handleRequestError,
    request
  } from 'src/core/utils/requests';

  import { getApiEndpoint } from 'src/core/utils/api-url-resolver';

  /**
   * `Options` type.
   */

  type Options = {
    locale: string
  };

  /**
   * Export `fetch$1`.
   */

  export async function fetch$1({ locale }: Options) {
    const endpoint = getApiEndpoint('');
    try {
      const { data } = await request.get(endpoint, {
        headers: acceptLanguageHeader(locale)
      });

      return data?.data;
    } catch (error) {
        handleRequestError(error);
    }
  }
  ```
</details>

<details>
  <summary>
    use query
  </summary>

  ```tsx
  const {
    data,
    isLoading,
    isSuccess
  } = use$1<>({ initialData: props.$2 })
  ```
</details>

<details>
  <summary>
    use request
  </summary>

  ```ts
  /**
   * Module dependencies.
   */

  import { QueryObserverBaseResult, useQuery } from 'react-query';
  import { fetch } from './fetch-$2';
  import { useMemo } from 'react';
  import { useRouter } from 'next/router';

  /**
   * `Props` type.
   */

  type Props<P> = QueryObserverBaseResult<P, unknown>;

  /**
   * `Options` type.
   */

  type Options<P> = {
    initialData?: P | null
  };

  /**
   * Action type.
   */

  export const actionType = ({ locale }): string => {
    return `locale-$2`
  ;};

  /**
   * `use$1` hook.
   */

  function use$1<P>(options?: Options<P>): Props<P> {
    const { locale } = useRouter();
    const variables = useMemo(() => ({ locale }), [locale]);
    const result = useQuery([actionType(variables), variables], () => {
      return fetch$1(variables);
    }, { initialData: options?.initialData });

    return result;
  }

  /**
   * Export `use$1` hook.
   */

  export default use$1;
  ```
</details>

### Styled Components

<details>
  <summary>
    styled
  </summary>

  ```tsx
  /**
   * `$1` styled component.
   */

  const $1 = styled.$2`
    $3
  `
  ```
</details>

<details>
  <summary>
    styled image
  </summary>

  ```tsx
  /**
   * `ImageWrapper` styled component.
   */

  const ImageWrapper = styled.div`
    overflow: hidden;
    padding-bottom: 100%;
    position: relative;
  `;
  ```
</details>

### Styled Tools

<details>
  <summary>
    ifProp
  </summary>

  ```tsx
  ifProp('$1', $2, $3)
  ```
</details>

<details>
  <summary>
    switchProp
  </summary>

  ```tsx
  ${switchProp('$1', {
    $2: css`
      $3
    `
  })}
  ```
</details>

### NextJs

<details>
  <summary>
    getServerSideProps
  </summary>

  ```tsx
  /**
   * Export `getServerSideProps`.
   */

  export async function getServerSideProps({ locale }) {
    const data = 'fetchSomething';

    if (!data) {
      return {
        notFound: true
      };
    }

    return {
      props: {
        data
      }
    };
  }
  ```
</details>

### Misc

<details>
  <summary>
    dok | docBlock
  </summary>

  ```ts
  /**
   * `$1`.
   */
  ```
</details>

<details>
  <summary>
    export const
  </summary>

  ```ts
  /**
   * Export `$1`.
   */

  export const $1 = $2
  ```
</details>

<details>
  <summary>
    export interface
  </summary>

  ```ts
  /**
   * Export `$1` interface.
   */

  export interface $1 {
    $2
  }
  ```
</details>

<details>
  <summary>
    export type
  </summary>

  ```ts
  /**
   * Export `$1` type.
   */

  export type $1 = {
    $2
  }
  ```
</details>

<details>
  <summary>
    interface
  </summary>

  ```ts
  /**
   * `$1` interface.
   */

  interface $1 {
    $2
  }
  ```
</details>

<details>
  <summary>
    isMobile
  </summary>

  ```tsx
  const isMobile = useBreakpoint('$1', 'max');
  ```
</details>

<details>
  <summary>
    lodash
  </summary>

  ```ts
  import $1 from 'lodash/$1';
  ```
</details>

<details>
  <summary>
    module dependencies
  </summary>

  ```ts
  /**
   * Module dependencies.
   */
  ```
</details>

<details>
  <summary>
    nextImageComponent
  </summary>

  ```tsx
  <Image
    alt={''}
    layout={'fill'}
    objectFit={'cover'}
    src={''}
  />
  ```
</details>

<details>
  <summary>
    type
  </summary>

  ```ts
  /**
   * `$1` type.
   */

  type $1 = {
    $2
  }
  ```
</details>
