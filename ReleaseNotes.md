# RumbaLean Release Notes


## 3.5.0 from 2026-10-03
* House keeping now runs once the interval has passed rather than only when the server
  has been idle for a full interval. Because it used to hang off Conga's timeout alone,
  and every event starts that window again, a busy server would put house keeping off
  indefinitely: idle connections were not reaped and `OnCongaTimeout` never fired.
  The interval is measured to the millisecond, and putting the clock back no longer
  suspends house keeping
* Error trapping reworked: the server loop, the connection threads, house keeping and the
  trap around `OnRequest` now act on the signal `HandleError` raises when it is done
  (`#.ErrorParms.signal`) and cut back to Rumba's own handler. Using `HandleError` is
  still optional.
* New method `GetConnectionOfThread`: tells an error handler running in the thread that
  crashed which connection - and therefore which request - it was working on. Connections
  now also keep the last block of data received, as it arrived, in `LastBlock`
* RumbaLean is from now on maintained independently of Carlisle's Rumba. The document
  "HowToSyncWithRumba.md" has gone.
* Several bug fixes

## 3.4.1 from 2026-09-09
* Although a correct version of Rumba was distributed with Plodder, 
  a wrong version (with the same version number, strangely) was released
* Error trapping problem in `ServerLoop` fixed
* Errors in `OnHeader` were trapped but not reported. They are now logged and a 500 is returned

## 3.4.0 from 2025-07-11
* In case no path for the Conga DLLs is specified RumbaLean now goes 
  for the default: the ones of the currently running version of Dyalog

## 3.3.2 from 2025-01-19
* Bug fix: VALUE ERROR in `ServerLoop`

## 3.3.1 from 2024-11-24
* `819⌶` replaced by `¯3 ⎕C`
* Bug fix: error trapping with HandleError brought back (Server only)

## 3.3.0 from 2024-04-20
* The changes made in versions 3.2.0 and 3.2.1 were erroneous and therefore reverted

## 3.2.1 from 2024-04-19
* Bug fix for a problem that was introduced with 3.2.0

## 3.2.0 from 2024-04-19
* Rumba crashed on non-Windows platforms in case the current directory had disappeared.

## 3.1.1 from 2023-05-20
* Proxy-related bug fix in Core.ConnectProxy
* Bug fixes
  * Passing a dot as path for the Conga DLLs did not work
  * The Conga DLLs might not be found if left to defaults
  * The file mime.cvs caused a problem

## 3.1.0 from 2023-05-02
* RumbaLean can now deal with a proxy, including elevating http to https.

## 3.0.3 from 2022-11-17
* Minor change to `WaitForData` in case the user interrupts Rumba and there are no threads running

## 3.0.2 from 2022-07-19
* Bug fix in `PercentDecode`

## 3.0.1 from 2022-06-24
* Two functions converted from dfns to tradfns as a workaround for a Dyalog bug (<02024>)

## 3.0.0 from 2022-06-10
* Conga 3.3 updated to Conga 3.4

## 2.1.2 from 2021-09-29
* The function `GetCurrentUTCHttpDate` threw spurious DOMAIN ERRORs

## 2.1.1 from 2021-08-08
* Call to `ErrorInRumba` now embraced by :Trap 0 because we have seen
  strange things there.

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




