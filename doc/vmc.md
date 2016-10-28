# Protocol Documentation
<a name="top"/>

## Table of Contents
* [vmc.proto](#vmc.proto)
 * [Allele](#org.ga4gh.vmc.Allele)
 * [Diplotype](#org.ga4gh.vmc.Diplotype)
 * [Genotype](#org.ga4gh.vmc.Genotype)
 * [Haplotype](#org.ga4gh.vmc.Haplotype)
 * [Interval](#org.ga4gh.vmc.Interval)
 * [IntervalEdit](#org.ga4gh.vmc.IntervalEdit)
 * [SequenceReference](#org.ga4gh.vmc.SequenceReference)
 * [SequenceReference.Namespace](#org.ga4gh.vmc.SequenceReference.Namespace)
* [Scalar Value Types](#scalar-value-types)

<a name="vmc.proto"/>
<p align="right"><a href="#top">Top</a></p>

## vmc.proto



<a name="org.ga4gh.vmc.Allele"/>
### Allele
Allele represents a single contiguous change

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sequence | [SequenceReference](#org.ga4gh.vmc.SequenceReference) | required | sequence reference (namespace and accession) |
| location | [Interval](#org.ga4gh.vmc.Interval) | required | location of sequence change |
| replacement | [string](#string) | required | replacement sequence; empty for deletion |


<a name="org.ga4gh.vmc.Diplotype"/>
### Diplotype
Diplotype represents a collection of haplotypes.

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| haplotypes | [Haplotype](#org.ga4gh.vmc.Haplotype) | repeated | phased changes; intervals should not overlap |


<a name="org.ga4gh.vmc.Genotype"/>
### Genotype
Genotype represents multiple changes at a single location

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sequence | [SequenceReference](#org.ga4gh.vmc.SequenceReference) | required | sequence reference (namespace and accession) |
| location | [Interval](#org.ga4gh.vmc.Interval) | required | location of sequence change |
| replacements | [string](#string) | repeated | replacement sequences; empty for deletions |


<a name="org.ga4gh.vmc.Haplotype"/>
### Haplotype
Haplotype represents a collection of phased changes on a single
reference.

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sequence | [SequenceReference](#org.ga4gh.vmc.SequenceReference) | required | sequence reference (namespace and accession) |
| interval_edits | [IntervalEdit](#org.ga4gh.vmc.IntervalEdit) | repeated | phased changes; intervals should not overlap |


<a name="org.ga4gh.vmc.Interval"/>
### Interval
Represents the definite (i.e., not fuzzy) location of a sequence
feature using an interval of interbase coordinates.

Interbase coordinates refer to the points *between* residues.  For
a sequence of length n, 0 ≤ start ≤ end ≤ n, where 0 refers to the
point before the start of the sequence, n refers to the point at
the end of the sequence.  An interval in which start == end is a
zero width point between two nucleotides.  See
http://gmod.org/wiki/Introduction_to_Chado#Interbase_Coordinates
for more information.

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| start | [uint64](#uint64) | required | start position |
| end | [uint64](#uint64) | required | end position |


<a name="org.ga4gh.vmc.IntervalEdit"/>
### IntervalEdit
IntervalEdit represents a located sequence change.

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| location | [Interval](#org.ga4gh.vmc.Interval) | required | location of sequence change |
| replacement | [string](#string) | required | replacement sequence; empty for deletion |


<a name="org.ga4gh.vmc.SequenceReference"/>
### SequenceReference
Sequence reference represents a reference to a sequence in a
database.

| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| namespace | [SequenceReference.Namespace](#org.ga4gh.vmc.SequenceReference.Namespace) | required | name of recognized sequence reference (enum?) |
| accession | [string](#string) | required | replacement sequence; empty for deletion |



<a name="org.ga4gh.vmc.SequenceReference.Namespace"/>
### SequenceReference.Namespace


| Name | Number | Description |
| ---- | ------ | ----------- |
| NCBI | 0 | versioned NCBI identifier, such as NM_000059.3 or NC_000001.10 |
| ENSEMBL | 1 | versioned Ensembl identifier, such as ENST00000380152.7 |
| LRG | 2 | Locus Reference Genome; http://www.lrg-sequence.org/ |
| MD5 | 100 | MD5 of sequence |
| SHA1 | 101 | SHA1 of sequence |
| SHA256 | 102 | SHA256 of sequence |
| SHA512 | 103 | SHA512 of sequence |
| SEGUID | 110 | seguid of sequence |
| SEQHASH | 111 | seqhash of sequence |





<a name="scalar-value-types"/>
## Scalar Value Types

| .proto Type | Notes | C++ Type | Java Type | Python Type |
| ----------- | ----- | -------- | --------- | ----------- |
| <a name="double"/> double |  | double | double | float |
| <a name="float"/> float |  | float | float | float |
| <a name="int32"/> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int |
| <a name="int64"/> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long |
| <a name="uint32"/> uint32 | Uses variable-length encoding. | uint32 | int | int/long |
| <a name="uint64"/> uint64 | Uses variable-length encoding. | uint64 | long | int/long |
| <a name="sint32"/> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int |
| <a name="sint64"/> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long |
| <a name="fixed32"/> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int |
| <a name="fixed64"/> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long |
| <a name="sfixed32"/> sfixed32 | Always four bytes. | int32 | int | int |
| <a name="sfixed64"/> sfixed64 | Always eight bytes. | int64 | long | int/long |
| <a name="bool"/> bool |  | bool | boolean | boolean |
| <a name="string"/> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode |
| <a name="bytes"/> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str |