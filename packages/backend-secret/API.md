## API Report File for "@aws-amplify/backend-secret"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import { AwsCredentialIdentityProvider } from '@aws-sdk/types';
import { BackendId } from '@aws-amplify/plugin-types';
import * as iam from 'aws-cdk-lib/aws-iam';
import { SSMServiceException } from '@aws-sdk/client-ssm';
import { UniqueBackendIdentifier } from '@aws-amplify/plugin-types';

// @public
export const getSecretClient: (credentialProvider?: AwsCredentialIdentityProvider) => SecretClient;

// @public
export type Secret = SecretIdentifier & {
    value: string;
};

// @public
export type SecretAction = 'GET' | 'SET' | 'REMOVE' | 'LIST';

// @public
export type SecretClient = {
    getSecret: (backendIdentifier: UniqueBackendIdentifier | BackendId, secretIdentifier: SecretIdentifier) => Promise<Secret>;
    listSecrets: (backendIdentifier: UniqueBackendIdentifier | BackendId) => Promise<SecretIdentifier[]>;
    setSecret: (backendIdentifier: UniqueBackendIdentifier | BackendId, secretName: string, secretValue: string) => Promise<SecretIdentifier>;
    removeSecret: (backendIdentifier: UniqueBackendIdentifier | BackendId, secretName: string) => Promise<void>;
    grantPermission: (resource: iam.IGrantable, backendIdentifier: UniqueBackendIdentifier, secretActions: SecretAction[]) => void;
};

// @public
export class SecretError extends Error {
    constructor(message: string, options?: {
        cause?: SecretErrorCause;
        httpStatusCode?: number;
    });
    // (undocumented)
    cause: SecretErrorCause;
    static fromSSMException: (ssmException: SSMServiceException) => SecretError;
    // (undocumented)
    httpStatusCode: number | undefined;
}

// @public (undocumented)
export type SecretErrorCause = SSMServiceException | undefined;

// @public
export type SecretIdentifier = {
    name: string;
    version?: number;
};

// (No @packageDocumentation comment for this package)

```