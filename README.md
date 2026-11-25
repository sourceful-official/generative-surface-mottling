# Generative surface mottling benchmark

[Open the benchmark table](benchmark.csv) · [Browse the images](images/)

The benchmark records how often six raters answered **Yes** to “Do you see mottling in this image?” Each row links one PNG to its vote counts and the author's separate expert judgment. Rows follow the original presentation order within the retained subset.

| View | Items | Majority Yes | Tied 3–3 | Majority No | Expert Yes |
| --- | ---: | ---: | ---: | ---: | ---: |
| Whole image | 100 | 30 | 18 | 52 | 48 |
| Surface crop | 239 | 66 | 38 | 135 | 128 |
| Total | 339 | 96 | 56 | 187 | 176 |

## Reading the labels

Raters saw one image at a time and could zoom and pan. For crops, they judged the visible photographic surface and ignored any flat grey mask. The six judgments per item give 2,034 votes in total (802 Yes and 1,232 No).

In a separate pass, the author viewed the original alongside a signed lightness residual to help identify subtle mottling in the original. The expert label covers every item. Of the 56 items tied in the original vote, the author judged 42 Yes and 14 No. All 56 retain their original tie in the majority column.

## Using the table

| Column | Meaning |
| --- | --- |
| `item_id` | Unique text identifier for this image or crop. It is also the PNG filename stem. |
| `image_file` | Path to the PNG relative to this README. |
| `whole_image_id` | Join to `item_id` to find the parent whole image. Whole images reference themselves. Use this key to keep related views together in evaluation splits. |
| `item_type`, `model` | View (`whole` or `crop`) and generation model recorded for the parent image. |
| `width`, `height`, `image_sha256` | Pixel dimensions and SHA-256 digest of the released PNG file. |
| `yes_votes`, `no_votes` | Original six-rater counts for this item. |
| `majority` | Yes or No for four or more matching votes, Tie for a 3–3 split. |
| `expert_label` | The author's residual-assisted judgment, Yes or No, recorded independently of the vote count. |

## Selection and integrity

The original trial contained 100 whole images and 674 native-resolution surface crops. This retrospective subset keeps every whole image and the 239 crops with identifiable lettering, numbers or deliberate graphics. The screen applied only to crops. Whole images and crops can show the same surface, and rates in this selected set depend on that sampling.

All 339 PNGs match the SHA-256 digests recorded in the benchmark analysis. Each pair of vote counts was checked against the original six judgments. Expert Yes counts were checked against the manuscript for each view and each possible Yes-vote count from zero to six.

## License

- Repository code and documentation are licensed under the [MIT License](LICENSE).
- The benchmark data in `benchmark.csv` and the PNGs in `images/` are licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE-DATA).
