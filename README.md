[![PyPI version](https://badge.fury.io/py/lds-merkle-proof-2019.svg)](https://badge.fury.io/py/lds-merkle-proof-2019)

# lds-merkle-proof-2019-py
[MerkleProof2019](https://w3c-dvcg.github.io/lds-merkle-proof-2019/) implementation in python

## Installation

```
pip install lds-merkle-proof-2019-bloxberg
```

## Usage

### Encoding
```python
from lds_merkle_proof_2019.merkle_proof_2019 import MerkleProof2019

mp2019 = MerkleProof2019()

json_proof = {
  "path": [
    { "right": "51b4e22ed024ec7f38dc68b0bf78c87eda525ab0896b75d2064bdb9fc60b2698" },
    { "right": "61c56cca660b2e616d0bd62775e728f50275ae44adf12d1bfb9b9c507a14766b" }
  ],
  "merkleRoot": "3c9ee831b8705f2fbe09f8b3a92247eed88cdc90418c024924be668fdc92e781",
  "targetHash": "c65c6184e3d5a945ddb5437e93ea312411fd33aa1def22b0746d6ecd4aa30f20",
  "anchors": [
    "blink:btc:testnet:582733d7cef8035d87cecc9ebbe13b3a2f6cc52583fbcd2b9709f20a6b8b56b3"
  ]
}

encoded_value = mp2019.encode(json_proof)
print(encoded_value) # b'zmz7LKNSJbePX9eJWLTaNA3X69vbLSiaJWJPVpFWznKg19Aeug3PQHFrkySKFvvGJhECwPMn947tzUFYnVMxbS428oLi5tw2HLKP9szAArV3TbfDSKXddpfV6fPBde6XN8FDbri2wGtYrgyzDXEaGu6QzzUd1GDMTcZ7c9FVFTb8k5v6crug5aLt2Sevap1gE9DS7ZUpfRMv8TQHiktNnQBGgc74g8soERFuziTDWoPGTu3Xb6bAs431DJpGGKHDenmFjkQFUJnwQ9nFKKowYnf9h8Gp8gcQmE78aoWhtEG4qV6Jaik8HhPTQX3dD7MQrXzY8GAHh8tKWQfscyGWb6w4FMpok13jBpZWpaPTVR5fMXsa1garazbMRL7xssnwEJ2gzrCDrGkFXb3JyDGoXMffAYKHUetADrCd3sZKW9k5jC5d6bMA5zSwbyeZE9BjaD27mTrJXSzguAZ1pKsghFztG5u5h6jLgBGMp2aPFopvESSnCA'
```

### Decoding
```python
from lds_merkle_proof_2019.merkle_proof_2019 import MerkleProof2019

mp2019 = MerkleProof2019()

encoded_value = b'zmz7LKNSJbePX9eJWLTaNA3X69vbLSiaJWJPVpFWznKg19Aeug3PQHFrkySKFvvGJhECwPMn947tzUFYnVMxbS428oLi5tw2HLKP9szAArV3TbfDSKXddpfV6fPBde6XN8FDbri2wGtYrgyzDXEaGu6QzzUd1GDMTcZ7c9FVFTb8k5v6crug5aLt2Sevap1gE9DS7ZUpfRMv8TQHiktNnQBGgc74g8soERFuziTDWoPGTu3Xb6bAs431DJpGGKHDenmFjkQFUJnwQ9nFKKowYnf9h8Gp8gcQmE78aoWhtEG4qV6Jaik8HhPTQX3dD7MQrXzY8GAHh8tKWQfscyGWb6w4FMpok13jBpZWpaPTVR5fMXsa1garazbMRL7xssnwEJ2gzrCDrGkFXb3JyDGoXMffAYKHUetADrCd3sZKW9k5jC5d6bMA5zSwbyeZE9BjaD27mTrJXSzguAZ1pKsghFztG5u5h6jLgBGMp2aPFopvESSnCA'

decoded_json = mp2019.decode(encoded_value)
print(decoded_json) # {'path': [{'right': '51b4e22ed024ec7f38dc68b0bf78c87eda525ab0896b75d2064bdb9fc60b2698'}, {'right': '61c56cca660b2e616d0bd62775e728f50275ae44adf12d1bfb9b9c507a14766b'}], 'merkleRoot': '3c9ee831b8705f2fbe09f8b3a92247eed88cdc90418c024924be668fdc92e781', 'targetHash': 'c65c6184e3d5a945ddb5437e93ea312411fd33aa1def22b0746d6ecd4aa30f20', 'anchors': ['blink:btc:testnet:582733d7cef8035d87cecc9ebbe13b3a2f6cc52583fbcd2b9709f20a6b8b56b3']}

```


# Development

## Run tests

```
./run_tests.sh
```

## Publishing To Pypi
- Create an account for [pypi](https://pypi.org) & [pypi test](https://test.pypi.org)
- Install [twine](github.com/pypa/twine) - `pip install twine`
- Increment version in `__init__.py`
- Remove current items in dist - `rm -rf dist/*`
- Build package - `python setup.py install`
- Build sdist - `python setup.py sdist`
- Run pypi test upload - `twine upload --repository-url https://test.pypi.org/legacy/ dist/*`
- Upload to pypi - `twine upload --repository-url https://upload.pypi.org/legacy/ dist/*`
