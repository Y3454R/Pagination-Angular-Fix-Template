# tempo

```html
<td>{{ (paginator.page - 1) * paginator.pageSize + i + 1 }}</td>
```

```html
<app-paginator
class="d-flex justify-content-between align-items-center flex-wrap"
[paginator]="paginator"
[isLoading]="isLoading"
(paginate)="paginate($event)"
></app-paginator>
```

```jsx
import { PaginatorState } from 'src/app/_metronic/shared/crud-table';
```

```jsx
paginator: PaginatorState = new PaginatorState().recalculatePaginator(0);
cargoClaimsTable:CargoClaim[] = [];
```

```jsx
this.paginator = new PaginatorState().recalculatePaginator(this.cargoClaims.length);
this.updateTableData();

```

```jsx
// pagination

paginate(paginator: PaginatorState) {

	this.cargoClaimsService.patchState({ paginator });
	
	this.updateTableData();

}

// Update table data based on current pagination state

updateTableData() {
	
	const startIndex = (this.paginator.page - 1) * this.paginator.pageSize;
	
	const endIndex = startIndex + this.paginator.pageSize;
	
	this.cargoClaimsTable = this.cargoClaims.slice(startIndex, endIndex);

}

```

```html
<div class="col">
	<label>Date</label>
	<input
		type="date"
		name="surveyBillDate"
		[(ngModel)]="surveyReport.surveyBillDate"
		class="form-control form-control-solid"
	/>
</div>

```