# RumbaLean Release Notes


## 2.1.2 from 2021-09-29

* The function `GetCurrentUTCHttpDate` threw spurious DOMAIN ERRORs

## 2.1.1 from 2021-08-08

* Call to `ErrorInRumba` now embraced by :Trap 0 because we have seen strange things there.

## 2.0.0 from 2021-06-16

* `URI` renamed to `RequestTarget`
* New Laguntza integrated for viewing the help
* All changes up to Rumba 0.1.10 integrated

### 1.0.3 from 2021-02-23
* Global `∆CONGA_DLL_PATH` introduced into: `Rumba.Core`; defaults to an empty vector.


### 1.0.2 from 2020-11-19

* Bug fixes:
  * Invalid guard removed from `ParseParameters`.
  * `ArchiveLog` wrongly used `⎕FUNTIE`. However, it does not make a difference in RumbaLean anyway.


### 1.0.1 from 2020-06-18

* Bug fix in Conga.X509Cert.FindDRC  (<01710>)

## 1.0.0 from 2020-03-12

* Fork from Rumba, based on version 0.1.6
